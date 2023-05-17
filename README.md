# Text-Excel
A spreadsheet is a two dimensional series of cells indexed by column letters and row numbers. A letter followed by a number identifies cells within spreadsheets (e.g., ”D13” or “F9”).  The cell designated by “C2” means the third column (labeled “C”) and the 2nd row, as in this partial printout of a spreadsheet
It's columns are from A-L and its rows range from 1-20. This program repeatedly accepts commands from the user (to change values stored in cells, perform operations on cells, etc.), until the user types ‘quit’, at which point the program will end.  After some commands, the program will re-print the updated spreadsheet, showing the changes caused by the user.  Commands are described as follows: F7 = “hi”
# sample inputs
B2 = ( 5-6 )
E9 = 5
C2 = 4.5
D1 = ( 2 * 7 / 3 )
D2 = ( 2 + 1 )
F5 = 6.2837%

Here are some key samples from this project:

# public Spreadsheet() {
		arr = new Cell[20][12];
		for(int i = 0;i<20;i++) {
			for(int j = 0;j<12;j++) {
				Cell cell = new EmptyCell(); 
				arr[i][j] = cell; 
			}
		}
	}
The constructor for the superclass of this project. It creates an array that stores the value of cells. The for loop fills each one with an EmptyCell to begin with.

# public SpreadsheetLocation(String cellName)
    {
    	this.cellName = cellName.toUpperCase();
    	this.col = cellName.charAt(0);
    	if(col>64) {
    		this.col = col-65; // - 65
    	}
    	this.row = Integer.parseInt(cellName.substring(1,cellName.length()))-1 ; 		
	}
  Constructor for the SpreadsheetLocation class. This creates fields for the row and column of a cell. It accepts a String such as "A20". It isolates the first char and stores it as an int in the "col" field. It also take the rest of the string and stores it as an int in the "row" field.
  
 # public ValueCell(double value) {
		super(value+"");
		this.value = (int)value;
	}
 This is the constructor for the ValueCell class. TextCell, FormulaCell, and PercentCell are all subclasses of it. It takes a double as the parameter and assigns it to the "value" field. 
 
# public String abbreviatedCellText() {
		String abbText = "" + super.value;
		
		if(abbText.length()>10) {
			return abbText.substring(0,10);
		}
		else {
			while(abbText.length()<10) {
				abbText+=" ";
			}
			abbText+="";
			return abbText;
		}
	}
 A method shared by the ValueCell class and its subclasses, this converts the value of the cell into a string of 10 characters, to be displayed in the grid. It uses the substsring method to shorten it if necessary.
 
# public Cell getCell(Location loc) 
	{
		return arr[loc.getRow()][loc.getCol()];  //ch5 testing a (Cell) cast	
	}
 A method within the Spreadsheet class. This returns the cell that is stored in the array field that contains all of the cells displayed within the grid. It uses the getRow() and getCol methods from the Location class to find and return the designated Cell.
