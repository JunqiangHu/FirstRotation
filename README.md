# FirstRotation 
**Content**
- [Intellectual Preparation](#preparation)
- [Codes and Results](#results)
- [Discussion](#discussion)
- [References](#references)

<a id='preparation'></a>
## Intellectual Preparation
  We want to use Reinforcement Learning to give some hints in the cognition. I read the important papers of DeepMind about Deep Q Network (DQN) and some updated versions of AlphaGo[<sup>1-4</sup>](#references1-4). What we want to do firstly is to reproduce the DQN results in Atari games, then based on the MCTS  we try to mimic human decision-making. 
  Why we focus on RL? There has been many significant attempts to imitate biological meanningful structures in computer. For example, the Tolman-Eichenbaum Machine use a complicated model to elucidate the place cell and the grid cell in hippocampus, the TEM also shows a capability to memorize the abstract structure in data[<sup>5</sup>](#references5). However, those imitation was restrained by the need of big data in real life or the complicated structures and prior knowledge. The RL methods have a superiority in the data production[<sup>6</sup>](#references6). The closed-loop data production can make a large amount of data in or like real conditions, that could contribute a lot.
  The core ideas of DQN are experience replay and target network. The former implies a similar role of memory in human and the latter uses a more robust way to have an accurate estimation of action value. 
    



<a id='results'></a>
## Codes and Results




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









