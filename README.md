Sudoku
======
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.*;



public class Fenetre extends JFrame implements ActionListener {

	/**
	 * 
	 */
	private static final long serialVersionUID = 1L;
	private JLabel label = new JLabel("Sudoku");
	private JMenuItem nouveau,correction,quitter,aide;
	private JMenuBar menu;
	private JMenu fichier,help;
	public static JButton[] b =new JButton[121];

	private String messageHelp="Bienvenue";

	public Fenetre(){

		Container c= getContentPane();
		c.setLayout(new GridLayout(11,11,5,5));

		JFrame jf =new JFrame();
		jf.setSize(800,600);
		jf.setResizable(true);
		jf.setLocationRelativeTo(null);
		jf.setTitle("Sudoku");

		menu = new JMenuBar();
		fichier = new JMenu("fichier");
		help = new JMenu("help");
		nouveau = new JMenuItem("nouveau");
		nouveau.addActionListener(this);
		correction = new JMenuItem("correction");
		correction.addActionListener(this);
		quitter = new JMenuItem("quitter");
		quitter.addActionListener(this);
		aide= new JMenuItem("?");
		aide.addActionListener(this);
		fichier.add(correction);
		fichier.add(nouveau);
		fichier.add(quitter);
		help.add(aide);
		menu.add(fichier);
		menu.add(help);
		setJMenuBar(menu);

		for(int i=0;i<b.length;i++){
			b[i]=new JButton("");
			b[i].setPreferredSize(new Dimension(100,50));
			b[i].setBackground(Color.white);
			c.add(b[i]);
			b[i].addActionListener(this);
		}
		for(int i = 3; i < 121; i+=11){
			b[i].setBackground(Color.gray);
		}
		for(int i = 7; i < 121; i+=11){
			b[i].setBackground(Color.gray);
		}
		for(int i = 33; i < 44; i++){
			b[i].setBackground(Color.gray);
		}
		for(int i = 77; i < 88; i++){
			b[i].setBackground(Color.gray);
		}


		//remplissage grille pour test
		/*int x = 0;
		for(int i = 0; i < 121; i++){
			while(b[i].getBackground()==Color.gray){
				i++;
			}
			if(i%11==0){
				x++;
			}
			b[i].setText(String.valueOf(x));
			x++;
			if(x == 10){
				x = 1;
			}
		}*/


		//Générator.Generate();
		//Generator.Generate();


		label.setPreferredSize(new Dimension (100,90));
		label.setHorizontalAlignment(SwingConstants.CENTER);

		jf.add(c,BorderLayout.CENTER);
		jf.add(label,BorderLayout.NORTH);
		jf.add(menu,BorderLayout.NORTH);

		jf.setVisible(true);

	}
	public void nouveauJeu(){
		for(int i=0;i<b.length;i++){
			b[i].setText("");;
			b[i].setPreferredSize(new Dimension(100,50));
			b[i].setBackground(Color.white);
		}
		for(int i = 3; i < 121; i+=11){
			b[i].setBackground(Color.gray);
		}
		for(int i = 7; i < 121; i+=11){
			b[i].setBackground(Color.gray);
		}
		for(int i = 33; i < 44; i++){
			b[i].setBackground(Color.gray);
		}
		for(int i = 77; i < 88; i++){
			b[i].setBackground(Color.gray);
		}
		Générator.Generate();
	}
	public void texthelp(){
		JOptionPane.showMessageDialog(null, messageHelp,"AIDE",JOptionPane.INFORMATION_MESSAGE);
	}

	public void actionPerformed(ActionEvent e){
		if(e.getSource()==nouveau)nouveauJeu();
		if(e.getSource()==quitter)System.exit(0);
		if(e.getSource()==aide)texthelp();

		if(e.getSource()==correction){
			Verif();
		}


		for(int i = 0; i < 121; i++){
			if(e.getSource()==b[i] && b[i].getBackground()==Color.white){
				String num = JOptionPane.showInputDialog(null, "Que désirez-vous entrer ?", "Saisie de nombres", JOptionPane.QUESTION_MESSAGE);
				b[i].setText(num);
			}
		}
	}



	public static void Verif(){
		boolean lignes = false;
		boolean c1 = false;
		boolean c2 = false;
		boolean c3 = false;
		boolean c4 = false;
		boolean c5 = false;
		boolean c6 = false;
		boolean c7 = false;
		boolean c8 = false;
		boolean c9 = false;


		//lignes

		for(int i = 0; i < 121; i+=11){
			c1 = false;
			c2 = false;
			c3 = false;
			c4 = false;
			c5 = false;
			c6 = false;
			c7 = false;
			c8 = false;
			c9 = false;
			for(int j = 0; j < 12; j++){
				if(i == 33 || i == 77){
					i += 11;
				}
				if(c1==false && i+j < 121){
					if(!b[j+i].getText().equals("1")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c1 = true;
						lignes = true;
					}
				}
				if(c2==false && i+j < 121){
					if(!b[j+i].getText().equals("2")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c2 = true;
						lignes = true;
					}
				}
				if(c3==false && i+j < 121){
					if(!b[j+i].getText().equals("3")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c3 = true;
						lignes = true;
					}
				}
				if(c4==false && i+j < 121){
					if(!b[j+i].getText().equals("4")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c4 = true;
						lignes = true;
					}
				}
				if(c5==false && i+j < 121){
					if(!b[j+i].getText().equals("5")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c5 = true;
						lignes = true;
					}
				}
				if(c6==false && i+j < 121){
					if(!b[j+i].getText().equals("6")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c6 = true;
						lignes = true;
					}
				}
				if(c7==false && i+j < 121){
					if(!b[j+i].getText().equals("7")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c7 = true;
						lignes = true;
					}
				}
				if(c8==false && i+j < 121){
					if(!b[j+i].getText().equals("8")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c8 = true;
						lignes = true;
					}
				}
				if(c9==false && i+j < 121){
					if(!b[j+i].getText().equals("9")){
						if(j == 12){
							lignes = false;
							break;
						}
					}
					else if (i % 11 == 0){
						c9 = true;
						lignes = true;
					}
				}
			}
			if(c1 == false || c2 == false || c3 == false || c4 == false || c5 == false || c6 == false || c7 == false || c8 == false || c9 == false){
				lignes = false;
			}
			if(lignes == false){
				JOptionPane.showMessageDialog(null, "Il y a une ou plusieurs erreurs dans les lignes.","AIDE",JOptionPane.WARNING_MESSAGE);
				break;
			}
			else if(i == 110){
				System.out.println("Lignes Ok !");
			}
		}


		//colones

		boolean colones = false;
		for(int i = 0; i < 11; i++){
			c1 = false;
			c2 = false;
			c3 = false;
			c4 = false;
			c5 = false;
			c6 = false;
			c7 = false;
			c8 = false;
			c9 = false;
			for(int j = 0; j < 121; j+=11){
				if(i == 3 || i == 7){
					i += 1;
				}
				if(c1==false){
					if(!b[j+i].getText().equals("1")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c1 = true;
						colones = true;
					}
				}
				if(c2==false){
					if(!b[j+i].getText().equals("2")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c2 = true;
						colones = true;
					}
				}
				if(c3==false){
					if(!b[j+i].getText().equals("3")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c3 = true;
						colones = true;
					}
				}
				if(c4==false){
					if(!b[j+i].getText().equals("4")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c4 = true;
						colones = true;
					}
				}
				if(c5==false){
					if(!b[j+i].getText().equals("5")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c5 = true;
						colones = true;
					}
				}
				if(c6==false){
					if(!b[j+i].getText().equals("6")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c6 = true;
						colones = true;
					}
				}
				if(c7==false){
					if(!b[j+i].getText().equals("7")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c7 = true;
						colones = true;
					}
				}
				if(c8==false){
					if(!b[j+i].getText().equals("8")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c8 = true;
						colones = true;
					}
				}
				if(c9==false){
					if(!b[j+i].getText().equals("9")){
						if(j == 121){
							colones = false;
							break;
						}
					}
					else{
						c9 = true;
						colones = true;
					}
				}				
			}
			if(c1 == false || c2 == false || c3 == false || c4 == false || c5 == false || c6 == false || c7 == false || c8 == false || c9 == false){
				colones = false;
			}
			if(colones == false){
				JOptionPane.showMessageDialog(null, "Il y a une ou plusieurs erreurs dans les colones.","AIDE",JOptionPane.WARNING_MESSAGE);
				break;
			}
			else if(i == 10){
				System.out.println("Colones Ok !");
			}
		}


		//carrés


		boolean carrés = false;
		c1 = false;
		c2 = false;
		c3 = false;
		c4 = false;
		c5 = false;
		c6 = false;
		c7 = false;
		c8 = false;
		c9 = false;

		for(int i = 0; i <= 96; i+=4){
			c1 = false;
			c2 = false;
			c3 = false;
			c4 = false;
			c5 = false;
			c6 = false;
			c7 = false;
			c8 = false;
			c9 = false;
			if(i == 12 || i == 56){
				i += 32;
			}
			for(int j = 0; j <= 24; j++){
				if(j == 3 || j == 14){
					j += 8;
				}
				if(c1 == false){
					if(!b[j+i].getText().equals("1")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c1 = true;
						carrés = true;
					}
				}
				if(c2 == false){
					if(!b[j+i].getText().equals("2")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c2 = true;
						carrés = true;
					}
				}
				if(c3 == false){
					if(!b[j+i].getText().equals("3")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c3 = true;
						carrés = true;
					}
				}
				if(c4 == false){
					if(!b[j+i].getText().equals("4")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c4 = true;
						carrés = true;
					}
				}
				if(c5 == false){
					if(!b[j+i].getText().equals("5")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c5 = true;
						carrés = true;
					}
				}
				if(c6 == false){
					if(!b[j+i].getText().equals("6")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c6 = true;
						carrés = true;
					}
				}
				if(c7 == false){
					if(!b[j+i].getText().equals("7")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c7 = true;
						carrés = true;
					}
				}
				if(c8 == false){
					if(!b[j+i].getText().equals("8")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c8 = true;
						carrés = true;
					}
				}
				if(c9 == false){
					if(!b[j+i].getText().equals("9")){
						if(j == 25){
							carrés = false;
							break;
						}
					}
					else{
						c9 = true;
						carrés = true;
					}
				}
			}


			if(c1 == false || c2 == false || c3 == false || c4 == false || c5 == false || c6 == false || c7 == false || c8 == false || c9 == false){
				carrés = false;
			}
			if(carrés == false){
				JOptionPane.showMessageDialog(null, "Il y a une ou plusieurs erreurs dans les carrés.","AIDE",JOptionPane.WARNING_MESSAGE);
				break;
			}
			else if(i == 96){
				System.out.println("Carrés Ok !");
			}
		}
		if(lignes == true && colones == true && carrés == true){
			JOptionPane.showMessageDialog(null, "Correct !","Bien joué",JOptionPane.INFORMATION_MESSAGE);
		}
	}
}
