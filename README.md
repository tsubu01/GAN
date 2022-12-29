# GAN
This is a Multi Purpose GAN (MP-GAN) playground I built to experiment with architectures and datasets.\
The main purpose in using this framework is to gain insights about GAN training and the structure of the latent space.\
I tested it both on images (mnist) and tabular data. To switch between tabular data and images you only need to change the\
model structure, not the internal flow.\
Usage:\
> pip3 install -r requirements.txt\
Then Run MP-GAN_Notebook.ipynb\
The GAN architecture can be controlled in the cell 'building the gan'.\
The folder ./models contains the file deep_model.py, which defines the API through which the user can build the GAN.\
The other file in ./models is gan_class.py that defines the GAN itself.\
The file gan_utils.py enables utility evaluation and exploring the data synthesized by the trained GAN. Some functions there are relevant to\
tabular data, and some are for image data.\

Some results:\
The image below was generated using a small GAN (D size 40k params, G size 1M params), training for ~600 epochs on MNIST.\
<img width="579" alt="image" src="https://user-images.githubusercontent.com/47942735/209480564-342538c2-2426-4d82-b189-b88e9702e8ae.png">
Next, is a comparison between 2 larger GANs (same G, but D 160k params), after 10, 20 and 50 epochs of training. Left: train from scratch,\
right: use predtrained D.\
<img width="718" alt="image" src="https://user-images.githubusercontent.com/47942735/209481169-36867ac0-6db0-4a00-bbfd-ad7702b43c75.png">
<img width="714" alt="image" src="https://user-images.githubusercontent.com/47942735/209481107-b79548fb-f125-492a-9d1a-8c741a6b8c85.png">
The two following images were generated by transforming points on a grid in the latent space:\
Interestingly, all the tests I've conducted showed that near the latent 0, the points do not transform to a meanfingful image. I hypothesize that the non-linearity of the generator (the Leaky ReLU is non-linear at 0) makes 0 a natural borderline region between image representation regions.
<img width="698" alt="image" src="https://user-images.githubusercontent.com/47942735/210015125-42fc318c-f879-4ee8-a236-c707fd4e705d.png">
