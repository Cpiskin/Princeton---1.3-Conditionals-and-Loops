import javax.imageio.ImageIO;
import java.awt.*;
import java.awt.image.BufferedImage;
import java.io.File;
import java.io.IOException;

public class Tile {

    public static void main(String[] args) {
        if (args.length != 3) {
            System.out.println("Usage: java Tile <image-file> <m> <n>");
            return;
        }

        String imageFileName = args[0];
        int m = Integer.parseInt(args[1]);
        int n = Integer.parseInt(args[2]);

        try {
            BufferedImage originalImage = ImageIO.read(new File(imageFileName));

            int originalWidth = originalImage.getWidth();
            int originalHeight = originalImage.getHeight();

            int newWidth = originalWidth * m;
            int newHeight = originalHeight * n;

            BufferedImage tiledImage = new BufferedImage(newWidth, newHeight, BufferedImage.TYPE_INT_ARGB);
            Graphics2D g2d = tiledImage.createGraphics();

            for (int i = 0; i < m; i++) {
                for (int j = 0; j < n; j++) {
                    g2d.drawImage(originalImage, i * originalWidth, j * originalHeight, null);
                }
            }

            g2d.dispose();

            // Save the tiled image
            ImageIO.write(tiledImage, "png", new File("tiled_image.png"));
            System.out.println("Tiled image saved as tiled_image.png");

        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
