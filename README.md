import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class RomanoParaInt {

    public static int AlgarismoRomanoParaInteiro(String s) {

        Map<Character, Integer> romanos = new HashMap<>();

        romanos.put('I', 1);
        romanos.put('V', 5);
        romanos.put('X', 10);
        romanos.put('L', 50);
        romanos.put('C', 100);
        romanos.put('D', 500);
        romanos.put('M', 1000);

        int resultado = 0;

        for (int i = 0; i < s.length(); i++) {

            int valorAtual = romanos.get(s.charAt(i));

            if (i < s.length() - 1) {

                int proximoValor = romanos.get(s.charAt(i + 1));

                if (valorAtual < proximoValor) {
                    resultado -= valorAtual;
                } else {
                    resultado += valorAtual;
                }

            } else {
                resultado += valorAtual;
            }
        }

        return resultado;
    }

    public static void main(String[] args) {

        // Passando argumento pela linha de comando
        if (args.length > 0) {

            String algarismos = String.join("", args).toUpperCase();

            int valor = AlgarismoRomanoParaInteiro(algarismos);

            System.out.println("Valor inteiro: " + valor);
            return;
        }

        // Entrada pelo teclado
        Scanner sc = new Scanner(System.in);

        System.out.print("Informe o algarismo romano: ");

        String algarismos = sc.nextLine().toUpperCase();

        int valor = AlgarismoRomanoParaInteiro(algarismos);

        System.out.println("Valor inteiro: " + valor);

        sc.close();
    }
}
