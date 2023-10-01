import java.awt.Color;

public class ColorConversion {

    public static void main(String[] args) {
        // Example 1: RGB to CMY
        int rgbColor = new Color(255, 0, 0).getRGB(); // Red in RGB
        Color cmyColor = convertRGBtoCMY(rgbColor);
        System.out.println("CMY Values: " + cmyColor);

        // Example 2: CMY to RGB
        Color rgbColor2 = convertCMYtoRGB(new Color(0, 1, 1)); // Cyan in CMY
        System.out.println("RGB Values: " + rgbColor2);
    }

    public static Color convertRGBtoCMY(int rgbColor) {
        int red = (rgbColor >> 16) & 0xFF;
        int green = (rgbColor >> 8) & 0xFF;
        int blue = rgbColor & 0xFF;

        float c = 1 - (red / 255f);
        float m = 1 - (green / 255f);
        float y = 1 - (blue / 255f);

        return new Color(c, m, y);
    }

    public static Color convertCMYtoRGB(Color cmyColor) {
        float c = cmyColor.getRed();
        float m = cmyColor.getGreen();
        float y = cmyColor.getBlue();

        int red = (int) ((1 - c) * 255);
        int green = (int) ((1 - m) * 255);
        int blue = (int) ((1 - y) * 255);

        return new Color(red, green, blue);
    }
}
