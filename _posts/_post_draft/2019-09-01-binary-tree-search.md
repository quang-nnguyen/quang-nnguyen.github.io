---
title: Binary Tree Search
category: 'fundamentals'
tags: [binary-tree-search, algorithm, data-structure]
classes: wide
---

Binary search is the most popular Search algorithm.It is efficient and also one of the most commonly used techniques that is used to solve problems.

If all the names in the world are written down together in order and you want to search for the position of a specific name, binary search will accomplish this in a maximum of 35 iterations.

<div id="sketch-holder"></div>

Binary search works only on a sorted set of elements. To use binary search on a collection, the collection must first be sorted.

When binary search is used to perform operations on a sorted set, the number of iterations can always be reduced on the basis of the value that is being searched. 


<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.7/p5.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.7/addons/p5.dom.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/p5.js/0.5.7/addons/p5.sound.min.js"></script>

<script>
// Tree object
function Tree() {
  // Just store the root
  this.root = null;
}

// Start by visiting the root
Tree.prototype.traverse = function() {
  this.root.visit(this.root);
}

// Start by searching the root
Tree.prototype.search = function(val) {
  var found = this.root.search(val);
  return found;
}

// Add a new value to the tree
Tree.prototype.addValue = function(val) {
  var n = new Node(val);
  if (this.root == null) {
    this.root = n;
    // An initial position for the root node
    this.root.x = width / 2;
    this.root.y = 16;
  } else {
    this.root.addNode(n);
  }
}
// Daniel Shiffman
// Nature of Code: Intelligence and Learning
// https://github.com/shiffman/NOC-S17-2-Intelligence-Learning

// Binary tree
var tree;


function setup() {
  const canvas = createCanvas(800, 600);
  canvas.parent('sketch-holder');
  
  // New tree
  tree = new Tree();

  // Add ten random values
  for (var i = 0; i < 50; i++) {
    tree.addValue(floor(random(0, 100)));
  }

  background(0);

  // Traverse the tree
  tree.traverse();

  // Search the tree for 10
  var result = tree.search(10);
  if (result == null) {
    console.log('not found');
  } else {
    console.log(result);
  }
}

// Daniel Shiffman
// Nature of Code: Intelligence and Learning
// https://github.com/shiffman/NOC-S17-2-Intelligence-Learning

// Node in the tree
function Node(val, x, y) {
  this.value = val;
  this.left = null;
  this.right = null;
  // How far apart should the children nodes be
  // This will be based on "level" in the tree
  this.distance = 2;
  // Now has a an xy position
  this.x = x;
  this.y = y;
}

// Search the tree for a value
Node.prototype.search = function(val) {
  if (this.value == val) {
    return this;
  } else if (val < this.value && this.left != null) {
    return this.left.search(val);
  } else if (val > this.value && this.right != null) {
    return this.right.search(val);
  }
  return null;
}

Node.prototype.visit = function(parent) {
  // Recursively go left
  if (this.left != null) {
    this.left.visit(this);
  }
  // Print out the value
  console.log(this.value);

  // Draw a line from the parent
  stroke(100);
  line(parent.x, parent.y, this.x, this.y);
  // Draw a circle
  stroke(255);
  fill(map(this.value,0,100,0,255),100,100);
  ellipse(this.x, this.y, 24, 24);
  noStroke();
  // Display the value
  fill(255);
  textAlign(CENTER);
  textSize(12);
  text(this.value, this.x, this.y + 4);

  // Go right
  if (this.right != null) {
    this.right.visit(this);
  }
}

// Add a new Node
Node.prototype.addNode = function(n) {
  // If it's less go left
  if (n.value < this.value) {
    // Is there nothing there? Place the node
    if (this.left == null) {
      this.left = n;
      // Exponentially shrink the distance between nodes for each level
      this.left.x = this.x - (width / pow(2, n.distance));
      this.left.y = this.y + (height / 12);
    // Keep going!
    } else {
      n.distance++;
      this.left.addNode(n)
    }
    // If it's more go right
  } else if (n.value > this.value) {
    // Is there nothing there? Place the node
    if (this.right == null) {
      this.right = n;
      this.right.x = this.x + (width / pow(2, n.distance));
      this.right.y = this.y + (height / 12);
    // Keep going!
    } else {
      n.distance++;
      this.right.addNode(n);
    }
  }
}
</script>