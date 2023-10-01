public class Squeeze {
    public static String squeezeSpaces(String input) {
        String result = "";
        boolean lastCharWasSpace = false;

        for (char c : input.toCharArray()) {
            if (c == ' ') {
                if (!lastCharWasSpace) {
                    result += c;
                    lastCharWasSpace = true;
                }
            } else {
                result += c;
                lastCharWasSpace = false;
            }
        }

        return result;
    }

    public static void main(String[] args) {
        // Example usage
        String inputString = "Hello   world!   How are    you?";
        String squeezedString = squeezeSpaces(inputString);
        System.out.println(squeezedString);
    }
}
