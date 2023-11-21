Dont forget these code is cutting the video into image by image and we are returning image by image also

We can add one or 2 more important import packages(like import torch,dlib) to the flowchart

`get_boundingbox` is returning the face.left(), face.top() and size_bb(which practically check for out of bound in the face with these formula int(max(face.right()-face.left(), face.bottom()-face.top() * scale )))
scale is a constant 1.3 which is used ti get the bigger face region

So `get_boundingbox` is generating a quadratic bounding box
the `get_boundingbox` takes in the arguement (face, width, height, the constant scale and a minsize which is none)



`preprocess_image` takes in image, and accepts cuda in our GPU to be true (Preprocesses the image such that it can be fed into our network. During this process we envoke PIL to cast it into a PIL image.) add import PIL

STEPS: image get reverted from BGR and then we cast it to PIL image


Our function `predict_with_model` takes the in the required input also, in the function we call our function `preprocess_image` with it required input
the model got fed in the `preprocess_image` function and produce a output that also got fed in nn.softmax(which is a standard library). we then append our result to prediction that is converted to int even tho it may want to return float.
These practically return prediction which can be fake(1) or real(0) and the output image




`test_full_image_network` takes input like our video path, model path, output path with 2 constant start_frame and end_frame and to check maybe our cude is true), dont forget the 3 path are given to these function from our terminal. 
 - Check maybe our output path is visible and it create it for us in the folder
 - make sure the output video being created is .avi(we can say high quality)
 - our model needed in predict_with_model is feeded to the model_path and it check if our model is instance(parallel) or cuda then it also check if the modelname is `xception` (not the model file name)
 - Select the font size on our output written output
 - You can write the assert if statement for the start_frame and the end_frame
 - label fake if prediction is 1 with color(0,255,0) else real (0,0,255)
 - if frame_num <= end_frame we break. we done




 Dont forget we can outlin our error in the flowchart also, like when a user make a mistake in the output or the dont complete it. We direct the path to an error and we check for all in our code.


