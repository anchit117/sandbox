# sandbox

Upload implementations for any set of buttons (from MS Word). 
Use Java Eclipse SE





// Not complete just a try.
package abc;

import java.awt.Font;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.event.FocusEvent;
import java.awt.event.FocusListener;
import java.awt.event.KeyEvent;
import java.awt.event.KeyListener;
import java.awt.event.MouseEvent;
import java.awt.event.MouseListener;

import javax.swing.JButton;
import javax.swing.JEditorPane;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JTextArea;
import javax.swing.JTextField;

public class sandBox extends JFrame implements ActionListener {
	
	JFrame f;
	JButton b;
	JButton i;
	JButton u;
	JTextArea ta;
	JLabel l1;
	JLabel l2;
	private static javax.swing.JTextArea tabs[] = new javax.swing.JTextArea [50]; 
	int a = 36;
	int clickBold = 0;
	int clickItalic=0;
	int k=0;
	int d=0;
	int tb=1;
	
	sandBox(String t)
	{		
		f=new JFrame(t);
		f.setLayout(null);
		
		b=new JButton("B");
		b.setBounds(100, 50, 50, 30);
		f.add(b);
		l1 = new JLabel();
		l1.setBounds(100, 0, 50, 40);
		f.add(l1);
		
		i=new JButton("I");
		i.setBounds(225, 50, 50, 30);
		f.add(i);
		l2 = new JLabel();
		l2.setBounds(225, 0, 50, 40);
		f.add(l2);
		
		u=new JButton("U");
		u.setBounds(350, 50, 50, 30);
		f.add(u);
		
		ta = new JTextArea();
		ta.setBounds(50, 150, 400, a);
		f.add(ta);
		
		for(int j=0;j<49;j++) // needs improvement
		{
			tabs[j] = new JTextArea();
			tabs[j].setBounds(50+k, 250, 8, 18);
			k+=8;
			f.add(tabs[j]);
		}
		

		for(d=0;d<47;d++)
		{
			tabs[d].addKeyListener(new KeyListener() {
			
			@Override
			public void keyTyped(KeyEvent e) {
				// TODO Auto-generated method stub
				
				
			}
			
			@Override
			public void keyReleased(KeyEvent e) {
				// TODO Auto-generated method stub
				try
				{
				   if(e.getKeyCode()!=KeyEvent.VK_BACK_SPACE)
				   {
				      tabs[tb].requestFocus();
				      tb+=1;
				   }
				}
				catch(NullPointerException ex)
				{
					System.out.println("\007");
				}
				catch(ArrayIndexOutOfBoundsException ep)
				{
					System.out.println("\007");
				}
				
			
			}
			
			@Override
			public void keyPressed(KeyEvent e) {
				// TODO Auto-generated method stub
				
			}
				
			}
		
		);
		}
		
		
			b.addMouseListener(new MouseListener() {
				
				@Override
				public void mouseReleased(MouseEvent arg0) {
					// TODO Auto-generated method stub
					
				}
				
				@Override
				public void mousePressed(MouseEvent arg0) {
					// TODO Auto-generated method stub
					
				}
				
				@Override
				public void mouseExited(MouseEvent arg0) {
					// TODO Auto-generated method stub
					l1.setText("");
					
				}
				
				@Override
				public void mouseEntered(MouseEvent arg0) {
					// TODO Auto-generated method stub
					String q = "BOLD";
					Font font = new Font("Arial",Font.BOLD,15);
					l1.setFont(font);
					l1.setText(q);
					
				}
				
				@Override
				public void mouseClicked(MouseEvent arg0) {
					// TODO Auto-generated method stub
					String fontType=ta.getFont().getFontName();
			        int style=Font.BOLD;
			        int size=ta.getFont().getSize();
			        Font font = new Font(fontType, style, size);
			        ta.setFont(font);
			        Font f = ta.getFont();
					if(clickBold == 0)
					{
					   ta.setFont(f.deriveFont(f.getStyle() | Font.BOLD));
			           clickBold=1;
					}
					else  // not able to convert bold text into normal yet
					{ 
				        ta.setFont(f.deriveFont(f.getStyle()&~Font.BOLD)); // not working yet
						clickBold=0;
					}
				}
			});
			
			i.addMouseListener(new MouseListener() {
				
				@Override
				public void mouseReleased(MouseEvent e) {
					// TODO Auto-generated method stub
					
				}
				
				@Override
				public void mousePressed(MouseEvent e) {
					// TODO Auto-generated method stub
					
				}
				
				@Override
				public void mouseExited(MouseEvent e) {
					// TODO Auto-generated method stub
					l2.setText("");
				}
				
				@Override
				public void mouseEntered(MouseEvent e) {
					// TODO Auto-generated method stub
					String q = "italic";
					Font font = new Font("Arial",Font.ITALIC,18);
					l2.setFont(font);
					l2.setText(q);
					
				}
				
				@Override
				public void mouseClicked(MouseEvent e) {
					// TODO Auto-generated method stub
					String fontType=ta.getFont().getFontName();
			        int style=Font.ITALIC;
			        int size=ta.getFont().getSize();
			        Font font = new Font(fontType, style, size);
			        ta.setFont(font);
					
				}
			});
			
		
		f.setBounds(350, 350, 500, 400);
		f.setVisible(true);
		f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
	}	
	
	public void actionPerformed(ActionEvent ae)
	{
		
	}
	
			
	public static void main(String args[])
	{
		sandBox obj = new sandBox("Testing");
	}

}
