# Elective
2017 estrada java 
package charlene;
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class Main extends JFrame{

    JButton submit, checkLetter; //button to submit a word and to check the letter
    JLabel realWord, credits, word; // actual word and word length
    JPasswordField secret; //secret word
    JTextField tempLetter;
    public Main(){
        GridLayout myGrid = new GridLayout(5,2); // rows and columns
        setLayout(myGrid); // adds left to right top to bottom
        JLabel myTitle = new JLabel("      JAVA HANGMAN");
        add(myTitle);
        credits = new JLabel("Length of word is: ");
        add(credits);
        word = new JLabel("     Enter Word");
        add(word);
        secret = new JPasswordField(10);
        add(secret);
        JLabel check = new JLabel("     Enter Letter");
        add(check);
        JTextField tempLetter = new JTextField(10);
        add(tempLetter);
        JLabel answer = new JLabel("Hangman Word");
        add(answer);
        realWord = new JLabel(" "); ///fingure this out
        add(realWord);
        submit = new JButton("Start");
        add(submit);
        checkLetter = new JButton("Submit Letter");
        add(checkLetter);

        handlerClass handle = new handlerClass();
        submit.addActionListener(handle);
        checkLetter.addActionListener(handle);
    }
    public class handlerClass implements ActionListener{
        @Override
        public void actionPerformed(ActionEvent event){
            if (event.getSource()==submit){
                String temp = secret.getText();
                int length = temp.length();
                temp.toLowerCase();
                credits.setText("The word has "+ length+ " letters");
                double array[];
               // array = new char[];
                //length.= array;
                realWord.setText(secret.getText());

            }
            if (event.getSource()==checkLetter){
                String letter = secret                             .getText();
                char tempChar[]= letter.toCharArray(); // turns into an array
                String second = tempLetter.getText();
                second.toLowerCase();
                char secondarray[] = second.toCharArray();
                int L;
                for (L=0; L<9; L++){
                    if (secondarray[0] != tempChar[L])
                    {
                        JOptionPane.showMessageDialog(null,"WHOOPS TRY AGAIN!", "OH NO",JOptionPane.INFORMATION_MESSAGE);
                        realWord.setText(" "+secondarray[0]);

                    }



                }

                //if(boolean==tempLetter){
                    //String cLetter = tempLetter.getText();

                }

            }
        }


public static void main(String[] args){
        Main run = new Main();
        run.setTitle("hangman");
        run.setVisible(true);
        run.setSize(800,800);
        run.setDefaultCloseOperation(EXIT_ON_CLOSE);
    }
}
