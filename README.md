# Hello-World
/*this is my first repository 
*jkasbdklbjkasdsa
*jkashdjksabfbkdsaj
*fgjshnklfsdnklfndsklf
*sdfkhksdlfnkldsnfklkl
*/
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
import java.awt.Font;
/*Project Automated Questioning system*/
class OnlineTest implements ActionListener
{
	JFrame frame;
	JLabel l;  
    JRadioButton jb[]=new JRadioButton[5];  
    JButton b1,b2,b3; 
    ButtonGroup bg;  
	int current=0;
	int[] count=new int[10];
	int result=0;
	OnlineTest()
	{
		current=0;
		frame=new JFrame("Online Test on Java");
		l=new JLabel();
		b1=new JButton("Previous");
		b2=new JButton("Next");
		b3=new JButton("BookMark");
		bg=new ButtonGroup();
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		for(int i=0;i<5;i++)  
        {  
            jb[i]=new JRadioButton();     
            frame.add(jb[i]);  
            bg.add(jb[i]);  
        } 
		frame.setLayout(null);
		frame.setSize(900,450);
		l.setBounds(50,30,700,60);
		l.setFont(new Font("TimesNewRoman", Font.BOLD, 17));
		for(int i=0,j=0;i<4;i++,j+=40)
		{
			jb[i].setFont(new Font("TimesNewRoman", Font.PLAIN, 15));
			jb[i].setBounds(60,80+j,170,50);
		}
		b1.setBounds(60,280,120,30);
		b2.setBounds(270,280,120,30);
		b3.setBounds(470,280,120,30);
		b1.setFont(new Font("TimesNewRoman", Font.PLAIN, 15));
		b2.setFont(new Font("TimesNewRoman", Font.PLAIN, 15));
		b3.setFont(new Font("TimesNewRoman", Font.PLAIN, 15));
		set();
		b1.setEnabled(false); 
		b1.addActionListener(this);
		b2.addActionListener(this);
		b3.addActionListener(this);
		frame.add(l);
		for(int i=0;i<4;i++)
			frame.add(jb[i]);
		frame.add(b1);
		frame.add(b2);
		frame.add(b3);
		frame.setVisible(true);
	}
	public void actionPerformed(ActionEvent ae)
	{
		 if(ae.getSource() == b2)  
        {  
			b1.setEnabled(true); 
            if(check())  
                count[current]=1;;  
            current++;  
            set();   
            if(current==9)  
            {    
				b3.setEnabled(false);
                b2.setText("Result");  
            }  
	
		}
		if(ae.getActionCommand().equals("Previous"))
		{
			if(current == 0)
			{
				b1.setEnabled(false);    
			}
			else
			{	
				current-=1;
				count[current]=0;
				System.out.println(current);
			}
			set();
		}
		if(ae.getActionCommand().equals("BookMark"))
		{
			JButton bm=new JButton("BookMark "+(current+1));
			bm.setBounds(700,40*(current+1),120,30);
			current++;
			set();
			frame.add(bm);
		}
		if(ae.getActionCommand().equals("Result"))  
        {  
            if(check())  
                count[current]=1;
            current++;  
            //System.out.println("correct ans="+count);  
			for(int i=0;i<10;i++)
			{
				if(count[i] == 1)
					result++;
			}
            JOptionPane.showMessageDialog(frame,"correct ans="+result);  
            System.exit(0);  
        }  
	}
	void set()
	{
		 jb[4].setSelected(true);  
		if(current==0)  
        {  
			b1.setEnabled(false);
            l.setText("Que1: Which one among these is not a primitive datatype?");  
            jb[0].setText("int");jb[1].setText("Float");jb[2].setText("boolean");jb[3].setText("char");   
        }  
        if(current==1)  
        {  
            l.setText("Que2: Which class is available to all the class automatically?");  
            jb[0].setText("Swing");jb[1].setText("Applet");jb[2].setText("Object");jb[3].setText("ActionEvent");  
        }  
        if(current==2)  
        {  
            l.setText("Que3: Which package is directly available to our class without importing it?");  
            jb[0].setText("swing");jb[1].setText("applet");jb[2].setText("net");jb[3].setText("lang");  
        }  
        if(current==3)  
        {  
            l.setText("Que4: String class is defined in which package?");  
            jb[0].setText("lang");jb[1].setText("Swing");jb[2].setText("Applet");jb[3].setText("awt");  
        }  
        if(current==4)  
        {  
            l.setText("Que5: Which institute is best for java coaching?");  
            jb[0].setText("Utek");jb[1].setText("Aptech");jb[2].setText("SSS IT");jb[3].setText("jtek");  
        }  
        if(current==5)  
        {  
            l.setText("Que6: Which one among these is not a keyword?");  
            jb[0].setText("class");jb[1].setText("int");jb[2].setText("get");jb[3].setText("if");  
        }  
        if(current==6)  
        {  
            l.setText("Que7: Which one among these is not a class? ");  
            jb[0].setText("Swing");jb[1].setText("Actionperformed");jb[2].setText("ActionEvent");  
                        jb[3].setText("Button");  
        }  
        if(current==7)  
        {  
            l.setText("Que8: which one among these is not a function of Object class?");  
            jb[0].setText("toString");jb[1].setText("finalize");jb[2].setText("equals");  
                        jb[3].setText("getDocumentBase");         
        }  
        if(current==8)  
        {  
            l.setText("Que9: which function is not present in Applet class?");  
            jb[0].setText("init");jb[1].setText("main");jb[2].setText("start");jb[3].setText("destroy");  
        }  
        if(current==9)  
        {  
            l.setText("Que10: Which one among these is not a valid component?");  
            jb[0].setText("JButton");jb[1].setText("JList");jb[2].setText("JButtonGroup");  
                        jb[3].setText("JTextArea");  
        }  
	}
	boolean check()  
    {  
        if(current==0)  
            return(jb[1].isSelected());  
        if(current==1)  
            return(jb[2].isSelected());  
        if(current==2)  
            return(jb[3].isSelected());  
        if(current==3)  
            return(jb[0].isSelected());  
        if(current==4)  
            return(jb[2].isSelected());  
        if(current==5)  
            return(jb[2].isSelected());  
        if(current==6)  
            return(jb[1].isSelected());  
        if(current==7)  
            return(jb[3].isSelected());  
        if(current==8)  
            return(jb[1].isSelected());  
        if(current==9)  
            return(jb[2].isSelected());  
        return false;  
    }  
}

public class OnlineTestDemo
{
	public static void main(String args[])
	{
		OnlineTest obj = new OnlineTest();
	}
}
