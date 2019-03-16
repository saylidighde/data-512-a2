
## Readme - Biblioteca Italiana
UW DATA 590 Project for Biblioteca Italiana

### Goal 

Biblioteca Italiana Seattle (BIS), an Italian library in Seattle is missing cover images for some books
in its digital catalog. The current process is to manually search and pick the right cover images through photographs of book covers. The aim of our project is to make this process more efficient. More specifically, our proposed deliverable is a pipeline that extracts the words on a cover image enabling BIS to search for the right one more quickly by typing in the title and author of a book.

### Data

* For the character extraction model, we generated a set of cover pages (.jpegs) using a combination of Italian authors, titles, font styles and font sizes to mimic real life pages.
* For the character prediction model, we used two data sources:
    * a. handwritten letters from the EMNIST dataset.
    * b. printed letters of varying fonts and emphases from the Chars74K dataset.

### Approach

* First, Computer Vision techniques are used to preprocess the cover image and identify prominent characters.
* Bounding boxes are drawn around these characters which are then cropped.
* A character prediction model predicts the most likely letter for each cropped image.
* The predicted strings are passed through a word segmentation model to get a list of most likely

### Model Pipeline

![image.png](attachment:image.png)

### Difficulties

1. Detecting regions of text was easy, but extracting the individual characters was challenging. A series of thresholding and dilation strategies helped solve this.
2. Having small and/or italic fonts made it difficult to differentiate between consecutive characters. Blowing up the image before extraction helped solve this issue.
3. Characters had to be extracted in order of their occurence on the page. We solved this by clustering the y-coordinates.

### Future Work

1. Letters with tittles like ‘i’ and ‘j’ are extracted as two characters. A way to group them together is required.
2. Real world images with significant noise give erroneous bounding boxes. Using better denoising is a possible fix.
3. Expanding classification model to predict special characters will make it more useful and generalized.
4. The word segmentation model works better on natural text than proper nouns like author names. Improving this model is essential to get better predictions.

### Recommendation

BIS’s pipeline of using volunteer-clicked images of book
covers for prediction will not be feasible for our current
model. We recommend adding an extra step of cropping the
image to remove unwanted elements or scanning the
particular page.

### Conclusion

While we did not achieve all the targets we set out for and are
not completely satisfied with the results, we have set in place
a pipeline that can be built on and improved.
Our key takeaway would be the experience gained from
working in the areas of Computer Vision, Neural Networks
and NLP, especially considering our team had little exposure
to these fields before the project.

### References

* [Peter Norvig’s NLP guide](https://techdevguide.withgoogle.com/resources/peter-norvigs-statistical-nlp/) 
* [OpenCV Documentation](https://docs.opencv.org/2.4/modules/refman.html)
* [Software Carpentry Blogs](https://software-carpentry.org/blog/) 
* [The Chars74K image dataset](https://docs.opencv.org/3.0-beta/modules/datasets/doc/datasets/tr_chars.html)
* [The EMNIST Dataset](https://www.nist.gov/itl/iad/image-group/emnist-dataset)
* [Tensorflow Documentation](https://www.tensorflow.org/api_docs)

### Acknowledgements

Special thanks to our sponsor, Dr. Luca Cazzanti, and our
professor, Dr. Megan Hazen and our TA, Zhe Liu for their
help and support.
