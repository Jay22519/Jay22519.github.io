# Image Processing Module

### Team -

| S. no | Name              | Enrollment no |
| ----- | ----------------- | ------------- |
| 1     |Ashish Lakra      | [BT18CSE038] |
| 2     | Rishabh Agrawal    | [BT18CSE054]  |
| 3     | Harshal Sable     | [BT18CSE075]  |
| 4     | Rishikesh Rachchh   | [BT18CSE091]  |

### Our project of Automatic Answer checking is divided into 2 modules ->

 1. Converting given input image file into text file
 2. Using the text file generated to find how correcrt the given answer is

**This page deals with the first module. The crux of it is to use optical character recognition (OCR) to extract text from handwritten answer sheet.**

### Overview

We are using Microsoft Azure Read API for text recognition from the uploaded document. However, the accuracy of such APIs is never perfect, so we are also using autocorrect/dictionary check as it will improve the accuracy in most cases.  

### Microsoft Azure Read API

The [Azure Computer Vision Read API](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/concept-recognizing-text) is Azure's latest OCR technology that extracts printed text (in several languages), handwritten text (English only), digits, and currency symbols from images and multi-page PDF documents. It's optimized to extract text from text-heavy images and multi-page PDF documents with mixed languages. It supports detecting both printed and handwritten text in the same image or document.  


### ```autocorrect``` Module and Levenshtein Distance

```autocorrect```<sup>[1]</sup> is a module in Python that takes a string as input and it replaces the words which it thinks are mispelled. Internally it uses the concept of Levenshtein distance <sup>[2]</sup> to find the closest matching word from the dictionary.  

The [Levenshtein distance](https://en.wikipedia.org/wiki/Levenshtein_distance#:~:text=Informally%2C%20the%20Levenshtein%20distance%20between,considered%20this%20distance%20in%201965.) is a number that tells you how different two strings are. The higher the number, the more different the two strings are.
For example, the Levenshtein distance between “kitten” and “sitting” is 3 since, at a minimum, 3 edits are required to change one into the other.  
- kitten → sitten (substitution of “s” for “k”)  
- sitten → sittin (substitution of “i” for “e”)  
- sittin → sitting (insertion of “g” at the end)  

An “edit” is defined by either an insertion of a character, a deletion of a character, or a replacement of a character.


### References
1. [Github Page for the autocorrect module](https://github.com/fsondej/autocorrect)  
2. [Understanding the Levenshtein Distance Equation](https://medium.com/@ethannam/understanding-the-levenshtein-distance-equation-for-beginners-c4285a5604f0)  
