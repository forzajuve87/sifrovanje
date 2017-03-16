package sifrovanje_vezba;

public class SifrarRotacija extends Sifrar{

	private int br_mesta;
	private String smer;
	
	// kostruktor
	public SifrarRotacija(Poruka sifra, int br_mesta, String smer) {
		super(sifra);
		this.br_mesta = br_mesta;
		this.smer = smer;
	}
	
	// set i get metode
	public void setMesta(int br_mesta) {
		this.br_mesta = br_mesta;
	}
	public void setSmer(String smer) {
		this.smer = smer;
	}
	public int getMesta() {
		return this.br_mesta;
	}
	public String getSmer() {
		return this.smer;
	}
	
	// polimorfni metod
	public Poruka sifruj() {
		String s = getPoruka().getTekst();
		
		if(smer.equals("desno")) {
			s = s.substring(s.length()-br_mesta, s.length()) + s.substring(0, s.length()-br_mesta);
		}
		else {
			s = s.substring(br_mesta, s.length()) + s.substring(0, br_mesta);
		}
		return new Poruka(s);
	}
	
	public String toString() {
		return "Rotiraj u smeru " + this.smer + " za " + this.br_mesta + ":\n" + super.toString();
	}
}
