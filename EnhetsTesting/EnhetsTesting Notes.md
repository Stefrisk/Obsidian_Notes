## 🧪 Summary: Unit Testing Guide with xUnit

This document is a comprehensive guide to unit testing in software development, especially using the xUnit framework in C#. It covers the purpose, types, structure, benefits, limitations, and practical exercises for writing unit tests.

## 🔍 Key Concepts

### ✅ Benefits of Automated Tests

- Cheap and fast to run
    
- Consistent results
    
- Early bug detection
    

### 🧱 Types of Automated Tests
 ![[Pasted image 20251103133543.png]]
## ⚙️ Unit Tests Explained

- No strict definition; varies by system
    
- Typically written by developers
    
- Should be fast and low-level
    
- In OOP: usually a class; in FP: a function or group of functions
    
- Developers/team decide what constitutes a "unit"


![[Pasted image 20251103133500 1.png]]
## 👍 Pros of Unit Testing

- Detects bugs early
    
- Saves time during testing
    
- Easier late-stage changes
    
- Builds confidence
    
- Documents functionality
    

## ⚠️ Cons and Limitations

- Can't catch all bugs
    
- Needs integration tests too
    
- Hard to write good tests
    
- Time-consuming
    
- May give false sense of security
    
- More code to maintain


![[Pasted image 20251103133514.png]]
## 🧪 AAA Pattern (Arrange-Act-Assert)

- **Arrange**: Prepare the object
    
- **Act**: Execute the test
    
- **Assert**: Verify the result
    

Optional steps:

- Cleanup after test
    
- Pre-assertion (affirm)
    

## 🧰 Testing Frameworks

- Avoid boilerplate
    
- Fast and optimized
    
- Examples: MSTest, NUnit, xUnit
    

### xUnit Highlights

- Free and open-source
    
- Created by NUnit v2 author
    
- Modern and flexible
    
- Sparse documentation but lots of community resources
    

## 🧪 xUnit Test Anatomy

[Fact]
public void TwoPlusTwoReturnsFour()
{
    var sut = new Calculator();
    var expected = 4;
    var actual = sut.Add(2, 2);
    Assert.Equal(expected, actual);
}


### Key Concepts

- `[Fact]`: Marks a method as a test
    
- `sut`: "System Under Test" – the object being tested
    
- `Assert`: Validates the outcome (pass/fail)

## 📏 Assert Methods Overview

### Numbers

- `Equal(expected, actual, precision)`
    
- `InRange(actual, min, max)`
    

### Strings

- `Equal(expected, actual, ignoreCase)`
    
- `Contains`, `StartsWith`, `Matches`
    

### Collections

- `Contains`, `Empty`, `All`
    

### Miscellaneous

- `Null`, `True`, `Same`, `IsType<T>`, `Throws<T>`
    

## 🧑‍💻 Exercises

### 1. Word and Letter Counter

Create a class `TextAnalyzer` with:

- `CountWords(string text)`
    
- `CountLetters(string text)`
    

Write xUnit tests for:

- Word count
    
- Letter count
    
- Empty string
    

### 2. Package Price Calculator

Handle two shipment types:

- **Package (box)**: Price = shortest side × longest side × weight + 10,000 öre
    
- **Cylinder (tube)**: Price = circumference × length × weight
    

Rules:

- Max weight: 20 kg
    
- Min weight for pricing: 2 kg
    
- Special fixed prices for small packages under 30 cm
    

Write unit tests for all calculations


![[Pasted image 20251103140102.png]] 


![[Pasted image 20251103140258.png]]
