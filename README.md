# Demenagement-Java-

• Créer un dossier (Dem2) depuis IntelliJ IDEA 
• Créer un package dans src (dem2)
• Dans le package dem2, créer une javaclass (Dem2), celui-ci constituera votre "main" comme ceci :

package dem2;

public class Dem2 {
    public static void main(String[] args) {
        Setup toto = new Setup();
        toto.setup();
    }
}

//////////////////////////////////////////////////////////////////

• Créer une javaclass (Setup), celui-ci servira de setup //perspicace girl// vous integrerez dedans tout votre code : 

package dem2;

public class Setup {
    String Newligne=System.getProperty("line.separator");
    int anLocal = 34;
    int camion = 0;
    int nvLocal = 0;
    double poids;
    int tas1 = 0;
    int tas2= 0;
    int tas3 = 0;
    int tas4 = 0;
    int i= 0;
    int[] capaBureau = {3, 4, 2, 1, 3, 2, 5, 2, 2, 1, 1, 3, 3, 3, 4};
    int[] bureauRemplir = {0,0,0,0,0,0,0,0,0,0,0,0,0,0};

    void setup() {

        while (camion<9 && anLocal>0)
        {

            chargement();//fonction chargement du camion

            System.out.print(" Un voyage de " + camion + " carton(s)");
            dechargement();//fonction déchargement
        }
        System.out.print(" Nombre de cartons dans l'ancien local "+ anLocal);
        System.out.print(" Nombre de cartons dans le camion " + camion);
        System.out.print(" Nombre de cartons dans le nouveau local ! "+ nvLocal);
        System.out.print(" Cartons inférieur ou égal à 1kg placés dans le tas n°1 --> "+ tas1 + Newligne + "Cartons compris entre 1 et 3kg placés dans le tas n°2 --> " + tas2 + Newligne + "Cartons compris entre 3 et 5kg placés dans le tas n°3 --> " + tas3 + Newligne + "Cartons strictement supérieur à 5kg placés dans le tas n°4 --> " + tas4);

        for (i=0; i<14; i++)

            if (nvLocal-capaBureau[i]>=0)

            {
                nvLocal=nvLocal-capaBureau[i];
                bureauRemplir[i]=capaBureau[i];
            }
            else if(nvLocal-capaBureau[i]<0)
            {
                bureauRemplir[i]=nvLocal;
                nvLocal=nvLocal-nvLocal;
            }


        System.out.print(Newligne +"Les cartons ont été dispatchés par bureau");
        System.out.print(bureauRemplir);

    }

    void chargement()//chargement du camion
    {
        while (camion<9 && anLocal>0)
        {
            camion++;

            anLocal--;
        }
    }
    void dechargement()//dechargement du maion
    {

        while (camion>0) {
            camion--;
            nvLocal++;
            poids();
        }

    }

    //peser
    void poids() {

        poids= Math.random() * 8;
        if (poids<=1)
        {
            tas1++;
        } else if (poids <=3) {
            tas2++;
        } else if (poids <=5) {
            tas3++;
        } else {
            tas4++;
        }
    }

    void remplirbureau()
    {
        while (nvLocal>0)

            for (int i=0; i<=14; i++)

                if (bureauRemplir[i]<capaBureau[i] && nvLocal>0)
                {
                    bureauRemplir[i]=bureauRemplir[i]+1;
                    nvLocal--;
                    System.out.print(bureauRemplir[i]);
                }



    }
}

////////////////////////////////////////////////////////////////////////////////////////
ENSUITE..
Pour exécuter ce programme, il faut d’abord le compiler. Ouvrez un shell (cmd, bash, …) et positionnez-vous dans le répertoire du fichier. Compilez et exécutez le programme comme ceci : 

javac *.java  //pour le compiler
java dem2.Dem2 // pour l'executer
