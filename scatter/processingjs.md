// GLOBAL VARIABLES
int w = 800;
int h = 600;
int p = 40;
int row = 151;
int col = 5;
String csv[];
String myData[][];
float xMax, yMax;

// SETUP
void setup () {

 // Set up the canvas
 size (w, h);

 // Load the dataset
 csv = loadStrings("/public/data/dlarge.csv");
 myData = new String[csv.length][col];
 for(int i=0; i<csv.length; i++) {
   myData[i] = csv[i].split(",");
 }

 // Find the max
 xMax = 0;
 yMax = 0;
 for(int i=1; i<myData.length; i++){
      if (xMax < float(myData[i][0])) {xMax = float(myData[i][0]);}
      if (yMax < float(myData[i][6])) {yMax = float(myData[i][6]);}
  }

 println(xMax,yMax);

}


// DRAW
void draw (){



  //Draw the scales  



  fill(255, 0, 0, 100);


  for(int i=1; i<myData.length; i++){
    float posX = map(float(myData[i][0]), 0, xMax, p, width - p);
    float posY = map(float(myData[i][6]), 0, yMax, height - p, p);
    //println(myData[i][0], posX,myData[i][6],posY);
    float markerSize = 10;
    ellipse(posX, posY, markerSize, markerSize);
  }

}

{% endhighlight %}


<canvas id="processing-canvas"> </canvas>
<script type="text/processing" data-processing-target="processing-canvas">

// GLOBAL VARIABLES
int w = 800;
int h = 600;
int p = 40;
int row = 151;
int col = 5;
String csv[];
String myData[][];
float xMax, yMax;

// SETUP
void setup () {

 // Set the canvas
 size (w, h);
 noLoop();

 // Load the iris csv
 csv = loadStrings("/public/data/dlarge.csv");
 myData = new String[csv.length][col];
 for(int i=0; i<csv.length; i++) {
   myData[i] = csv[i].split(",");
 }

 // Find the max
 xMax = 0;
 yMax = 0;
 for(int i=1; i<myData.length; i++){
      if (xMax < float(myData[i][0])) {xMax = float(myData[i][0]);}
      if (yMax < float(myData[i][6])) {yMax = float(myData[i][6]);}
  }
}


// DRAW
void draw (){



  //Draw the scales  



  fill(255, 0, 0, 100);


  for(int i=1; i<myData.length; i++){
    float posX = map(float(myData[i][0]), 0, xMax, p, width - p);
    float posY = map(float(myData[i][6]), 0, yMax, height - p, p);
    //println(myData[i][0], posX,myData[i][6],posY);
    float markerSize = 10;
    ellipse(posX, posY, markerSize, markerSize);
  }

}
