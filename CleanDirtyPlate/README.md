This workshop is pretty challlenging because my data is very limitted. Clean and dirty samples have only 20 and 20 images while test data is 700. To tell the model which one is clean/dirty is the challenging part in this input.

What i did in the first commit (cleandirtyestimation-pytorch-resnet.ipynb):
> I found new dataset that offers the same plates without background.
> 
> Implement it into my existig data so that it doubled. But it could be weird because one pattern is present with background and without background. It sounds weird for me at the first. But in result, my test accuracy is 88 percent!
> 
> Transform contents are not wide. I tried to enrich the inputs so that the model could keep learning until the very end of epoch.
> 
> In this section, i have used GPU.

then I made a decision of making my own background remover so that I dont get images without background from somewhere else. In addition to that, one image with bg and without bg sounds weird for me. So i dont want double my data in this way. Instead, i would enrich the data transform so that input would be augmented.
what i did here(CleanDirtyEstimation (GrabCut).ipynb):
> I refused to copy someone else's data. I created my own way for removing background with the help of using cv2.GrabCut()
> I test what transform in train and val could be reasonable for model. I gave some varients and I printed some images of train and val so I saw that important feature is not lost after transform.
> I fixed some issues that i had not noticed in the first commit. --> i did not notice that random.choice is not iterating in each epoch. After got it, i inserted this snippet in epoch loop.
>
>  I got %83 accuracy in this way.
>
> One question: https://discuss.pytorch.org/t/gpu-gives-different-results-than-cpu-in-training-the-model/217422 
