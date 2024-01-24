# Unaligned RGBT Semantic Segmentation
The affine transformation~\cite{xue2020affine} of a 2D image, denoted as $ \mathbf{M} $, is a composite of a linear transformation $ \mathbf{M_1} $ and a translation transformation $ \mathbf{M_2} $.
Linear transformations comprise rotation, reflection, shearing, and scaling and adhere to the closed principle of addition and multiplication.
As a result, the combination of different linear transformations remains a linear transformation. 
\begin{equation}
	\label{Eq.aff}
	\mathbf{M_1}=\left[\begin{array}{ll}
		a & b \\
		c & d
	\end{array}\right], ~~
	\mathbf{M_2}=\left[\begin{array}{l}
		e \\
		f
	\end{array}\right].
\end{equation}

In \eqnref{Eq.aff}, the affine transformation matrix can be formalized as $\mathbf{M} = \left[\mathbf{M_1};\mathbf{M_2} \right] \in \mathbb{R}^{2 \times 3}$.
Specifically, we randomly select three non-collinear points $ S=\{ s_i\}^{3}_{i=1} $ in the image and apply a random deformation to them to obtain the transformed points $T=\{ t_i\}^{3}_{i=1}$.
As shown in \figref{Fig.deformation}, we set the deformation strength $ k $ to adjust the affine transformation. The displacement range of each point $s_i = (x, y)^\top$ is randomly chosen from the interval $[-k, k]$. In U-MFNet datasets, $ k $ is set to 20 pixels.
Then the affine transformation process of $ S \rightarrow T $ can be expressed as:  
$t_i = \mathbf{M_1} \cdot s_i + \mathbf{M_2}.$$  
Given two point sets $ (S, T) $ before and after deformation, we can use the OpenCV library function to calculate the affine transformation matrix $ \mathbf{M} $.
Finally, we apply this $ \mathbf{M} $ matrix to the input image to obtain the output image after the affine transformation.

To create our new unaligned RGB-T SS benchmark, \textit{i.e.} U-MFNet dataset, we applied the aforementioned tools to deform the thermal images in the MFNet dataset, while keeping the RGB images unaltered.

![image](/VisionVerse/Unaligned-RGBT-Semantic-Segmentation/blob/main/deformation.jpg)  
**Fig. 1** Thermal images with different degrees of deformation were obtained with different $k$. The higher the value of $k$, the stronger the affine deformation in the image.


## New Unaligned Benchmark
- [Baidu Netdisk]()
