# 5-
分形树
void setup(){
  size(500,500);
  stroke(255);
}

void draw(){
  background(0);
  Tree(width/2,height,new PVector(0,-mouseX));
}


void Tree(float x, float y, PVector branch){
 if(branch.mag()>5){
   
    PVector ps = new PVector(x,y);
 
    PVector pe = ps.get();
   
    pe.add(branch);
  
    line(ps.x,ps.y,pe.x,pe.y);
    

    PVector br1 = branch.get();
    
    br1.mult(0.8);
 
    br1 = ROT(br1,radians(mouseY));
 
    Tree(pe.x,pe.y,br1);
    
  
    PVector br2 = branch.get();
    br2.mult(0.5);
    br2 = ROT(br2,radians(-mouseX));
    Tree(pe.x,pe.y,br2);
  }
}


PVector ROT(PVector p,float ang){
  PVector pr = new PVector(p.x*cos(ang)-p.y*sin(ang),p.x*sin(ang)+p.y*cos(ang));
  return pr;
}
