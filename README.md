# FirstRotation 
**Content**
- [Intellectual Preparation](#preparation)
- [Codes and Results](#results)
- [Discussion](#discussion)
- [References](#references)

<a id='preparation'></a>
## Intellectual Preparation
&ensp;&ensp;We want to use Reinforcement Learning to give some hints in the cognition. I read the important papers of DeepMind about Deep Q Network (DQN) and some updated versions of AlphaGo[<sup>1-4</sup>](#references1-4). What we want to do firstly is to reproduce the DQN results in Atari games, then based on the MCTS  we try to mimic human decision-making.  
&ensp;&ensp;Why we focus on RL? There has been many significant attempts to imitate biological meanningful structures in computer. For example, the Tolman-Eichenbaum Machine use a complicated model to elucidate the place cell and the grid cell in hippocampus, the TEM also shows a capability to memorize the abstract structure in data[<sup>5</sup>](#references5). However, those imitation was restrained by the need of big data in real life or the complicated structures and prior knowledge. The RL methods have a superiority in the data production[<sup>6</sup>](#references6). The closed-loop data production can make a large amount of data in or like real conditions, that could contribute a lot.  
&ensp;&ensp;The core ideas of DQN are experience replay and target network. The former implies a similar role of memory in human and the latter uses a more robust way to have an accurate estimation of action value. We estimate the trained model also mimic human brain, which means it also has a property of sparse coding. The sparse coding properties has been tested in CNN and GAN for image classification and image generation[<sup>7</sup>](#references7), but there has been lack in the research of sparse coding properties in Reinforcement Learning. That's what we want to test further.  
<a id='results'></a>
## Codes and Results
&ensp;&ensp;All codes are in python and the Deep learning package we use is pytorch. The basic framework is from updated codes in [zhihu](https://zhuanlan.zhihu.com/p/124593949). Most parameters are same as the [Ref.1](#references1-4), except the training frames. For simplicity, all the codes and related figures are zipped in model_training.rar and model_validation.rar. The figures in this report are copied to the file folder Figure.  
&ensp;&ensp;The basic structure of value prediction part in DQN is shown below and is simple. After three convolution layers to extract information, the output is then used for prediction after two layers of fully-connection. 
![](https://github.com/wublubd/FirstRotation/blob/main/Figures/model_structure.png?raw=true)
&ensp;&ensp;The training results are shown below. I focused on Pong, Breakout and SpaceInvaders three games. Pong and Breakout are two similar games which need a ball to hit on the bricks.  
### Pong
&ensp;&ensp;The trainnig result is fairly good in this parameters. To confirm the ability of the model to predict the state, I also hooked out the last hidden layer and designated the highest action value as the state value, and then showed the plot of different states and its state values.  
![](https://github.com/wublubd/FirstRotation/blob/main/Figures/pong/training_result.png?raw=true)  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/pong/state_profile_pong.png?raw=true"/></div>  
&ensp;&ensp;The actual state could show a trajectory, which may represents the pseudotime state changes after taking actions. I checked for the exact state change and we could tell the model can play the game well to get definate success. Also, the high state value implies a score within 30 frames while the low state value not.  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/pong/pong_high_value.gif?raw=true"/></div>  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/pong/pong_low_value.gif?raw=true"/></div>  
&ensp;&ensp;The above figure describes the following 30 frames after the red dot circled state with high value, while the below figure describes the following 30 frames after the grey dot circled state with low value.  

### Breakout
&ensp;&ensp;The trainnig result is not so good as that in Pong in this parameters. The most severe problem of RL is the high dependency of the environment and hyper parameters.  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/breakout/training_result.jpg?raw=true"/></div>
&ensp;&ensp;The model can play the game since the loss is converged and the reward is some high, but indeed the model couldn't clear all the bricks. The state profile is more messy but it still could indicate the value of state.  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/breakout/state_profile_breakout.png?raw=true"/></div>  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/breakout/breakout_high_value.gif?raw=true"/></div>  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/breakout/breakout_low_value.gif?raw=true"/></div>  
&ensp;&ensp;The middle figure describes the following 30 frames after the red dot circled state with high value, while the below figure describes the following 30 frames after the grey dot circled state with low value. The high value indiactes a hit on the brick while the low value directly describe a missing case.  
&ensp;&ensp;Since the similarity between Pong and Breakout, could we use the training model of Pong to transfer learnning the Breakout game? The feature extraction step in the convolutional layer may be similar and it could achieve a few-shot learning for this similar game. 
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/breakout_transfer/training_result.jpg?raw=true"/></div>  
&ensp;&ensp;The result partly match our hypothesis. The reward in each step increase early than that without transfer-learning, and the loss seems more stable although there still has been some collapses, but they are rare.   

### SpaceInvaders
&ensp;&ensp;The trainnig result is worse in this parameters. We also try to transfer the Pong model into this game, but result is also bad. Maybe the differences between Pong and SpaceInvaders are so many that the best parameters and weights differ a lot.  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/spaceinvaders/training_result.jpg?raw=true"/></div>  
<div align="center"><img src="https://github.com/wublubd/FirstRotation/blob/main/Figures/spaceinvaders_transfer/training_result.jpg?raw=true"/></div>  

<a id='discussion'></a>
## Discussion





<a id='references'></a>
## References
<a id='references1-4'></a>
1.Mnih, V., Kavukcuoglu, K., Silver, D., Rusu, A.A., Veness, J., Bellemare, M.G., Graves, A., Riedmiller, M., Fidjeland, A.K., Ostrovski, G., Petersen, S., Beattie, C., Sadik, A., Antonoglou, I., King, H., Kumaran, D., Wierstra, D., Legg, S., Hassabis, D., 2015. Human-level control through deep reinforcement learning. Nature 518, 529–533.. doi:10.1038/nature14236  
2.Silver, D., Schrittwieser, J., Simonyan, K., Antonoglou, I., Huang, A., Guez, A., Hubert, T., Baker, L., Lai, M., Bolton, A., Chen, Y., Lillicrap, T., Hui, F., Sifre, L., Van Den Driessche, G., Graepel, T., Hassabis, D., 2017. Mastering the game of Go without human knowledge. Nature 550, 354–359.. doi:10.1038/nature24270  
3.Silver, D., Hubert, T., Schrittwieser, J., Antonoglou, I., Lai, M., Guez, A., Lanctot, M., Sifre, L., Kumaran, D., Graepel, T., Lillicrap, T., Simonyan, K., Hassabis, D., 2018. A general reinforcement learning algorithm that masters chess, shogi, and Go through self-play. Science 362, 1140–1144.. doi:10.1126/science.aar6404  
4.Schrittwieser, J., Antonoglou, I., Hubert, T., Simonyan, K., Sifre, L., Schmitt, S., Guez, A., Lockhart, E., Hassabis, D., Graepel, T., Lillicrap, T., Silver, D., 2020. Mastering Atari, Go, chess and shogi by planning with a learned model. Nature 588, 604–609.. doi:10.1038/s41586-020-03051-4  
<a id='references5'></a>
5.Whittington, J., Muller, T., Mark, S., Chen, G., Barry, C., Burgess, N., & Behrens, T. , 2020. The Tolman-Eichenbaum Machine: Unifying Space and Relational Memory through Generalization in the Hippocampal Formation. Cell. 183, 1249-1263.. doi:10.1016/j.cell.2020.10.024
<a id='references6'></a>
6.De Melo, C., Torralba, A., Guibas, L., DiCarlo, J., Chellappa, R., & Hodgins, J. , 2022. Next-generation deep learning based on simulators and synthetic data. Trends in Cognitive Sciences 26, 174-187.. doi:10.1016/j.tics.2021.11.008
<a id='references7'></a>
7.Bau, D., Zhu, J.-Y., Strobelt, H., Lapedriza, A., Zhou, B., Torralba, A., 2020. Understanding the role of individual units in a deep neural network. Proceedings of the National Academy of Sciences 117, 30071–30078.. doi:10.1073/pnas.1907375117








