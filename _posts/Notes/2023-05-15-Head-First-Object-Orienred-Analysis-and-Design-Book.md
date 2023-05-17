---
title: "Head First Object Oriented analysis & Design Notes"
classes: wide
header:
  teaser: /assets/images/Blogs/Graduation-Project-Diray/head_first_object_oriented_analysis_and_design.jpg
ribbon: ForestGreen
description: "Head First OOA&D book notes and reviwe"
categories:
  - Learning Notes
toc: false
---

# Chapter 1: Great Software Begins Here

this chapter starts with `what is the great software?` question and going to discuss it with a deferent point of views. For example 
- The `customer friend` sees that the great software does what the customer wants it to do and doesn't give un expected result when we use it in a new way.
- The `Object-Oriented Programming` guy sees that the great software has no code duplication, each object controls its own behavior, and finally easy to be extended.
- The `Design Pattern` guy sees that the great software is what used a tried-and-true design patterns and principles. Objects are loosely coupled, Open for extension but closed for modifications. finally the code in the software must be reusable.
- A `Computer science` student in BFCAI that called Hossam Hamdy sees that the great software is the one which following the best design practices and design patterns to not re invent the wheel again, that software that respect customer requirements but in the same time we don't ignore the engineering side.

The Authors provide an approach for writing a great software with a simple steps:
**1. Make sure your software does what customer wants it to do.**
**2. Apply basic OO principles to add flexibilities.**
**3. Strive for a maintainable reusable design.**

In this chapter the authors learn me a new thing about `Encapsulation`, we can use it not only for information hiding, but also we can use it to remove duplicated codes. in the following code snippet we have the Guitar class that used in a `ArrayList <Guitar> search(Guitar guitar)` that implemented to take each class data member and compare with the client needs. 

```java
public class Guitar {  
    private String serialNumber;  
    private double price;  
    private Builder builder;  
    private String model;  
    private Type type;  
    private Wood backWood;  
    private Wood topWood;  
    public String getSerialNumber() {return serialNumber;}  
    public void setSerialNumber(String serialNumber) {this.serialNumber = serialNumber;}
    public double getPrice() {return price;}  
    public void setPrice(double price) {this.price = price;}  
    public Builder getBuilder() {return builder;}  
    public void setBuilder(Builder builder) {this.builder = builder;}  
    public String getModel() {return model;}  
    public void setModel(String model) {this.model = model;}  
    public Type getType() {return type;}  
    public void setType(Type type) {this.type = type;}  
    public Wood getBackWood() {return backWood;}  
    public void setBackWood(Wood backWood) {this.backWood = backWood;}  
    public Wood getTopWood() {return topWood;}  
    public void setTopWood(Wood topWood) {this.topWood = topWood;}  
 }
 ```


The problem is that the client doesn't really care about guitar serial number or price so that he doesn't provide the search method with this information which make the search method doesn't do its job properly because some data members are Null.
so that we can use the Encapsulation to separate the not necessary data from the Guitar object to a new object used for searching such as *GuitarSpec* that hold all necessary information about the target guitar.


The new Guitar Class code: 
```java
public class Guitar {  
    private String serialNumber;  
    private double price;
    // each guitar object must have a GuitarSpec object to descripe it.
    private GuitarSpec guitarSpec;
    public String getSerialNumber(){
	    return serialNumber;
	}  
    public void setSerialNumber(String serialNumber) {
	    this.serialNumber = serialNumber;
	} 
    public GuitarSpec getGuitarSpec() {
	    return serialNumber;
	}  
    public void setGuitarSpec(GuitarSpec guitarSpec) {
	    this.guitarSpec = guitarSpec;
	}
 }
```

The GuitarSpec Class code: 
```java
public class GuitarSpec {  
    private Builder builder;  
    private String model;  
    private Type type;  
    private Wood backWood;  
    private Wood topWood;  
    public Builder getBuilder() {return builder;}  
    public void setBuilder(Builder builder) {this.builder = builder;}  
    public String getModel() {return model;}  
    public void setModel(String model) {this.model = model;}  
    public Type getType() {return type;}  
    public void setType(Type type) {this.type = type;}  
    public Wood getBackWood() {return backWood;}  
    public void setBackWood(Wood backWood) {this.backWood = backWood;}  
    public Wood getTopWood() {return topWood;}  
    public void setTopWood(Wood topWood) {this.topWood = topWood;}  
 }
```

With this approach we have a good design because in the future if we wanna add a new prosperity to the Guitar we don't need to change the guitar class each time we have a new changes, we just need to add it into the GuitarSpec and the `search()` method will do it's job. we separate application's parts and encapsulate the part tat might vary/change away from the parts that will stay the same.
**`Anytime you see duplicate code, look for a place to encapsulate`**.

**Delegation** The act of one object forwarding an operation to another object, to be performed on behalf of the first object. such as `.equals()` method in java. delegation enables the code reusability, and make it **loosely coupled** (the object have a specific job to do and they do only that job).

| Idiom | Description |
| :---: | :---: |
| Functionality | Without me, you’ll never actually make the customer happy. No matter how well-designed your application is, I’m the thing that puts a smile on the customer’s face |
| Flexibility | Use me so that your software can change and grow without constant rework. I keep your application from being fragile |
| Encapsulation | You use me to keep the parts of your code that stay the same separate from the parts that change; then it’s really easy to make changes to your code without breaking everything |
| Design Pattern | I’m all about reuse and making sure you’re not trying to solve a problem that someone else has already figured out. |

