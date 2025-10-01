[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/y12QcJaO)
# HW 2: From Notebooks to Research Packages

_This repository is public so that Binder can find it. All code and data is based on the original [LIGO Center for Open Science Tutorial Repository](https://github.com/losc-tutorial/LOSC_Event_tutorial). This repository is a class exercise that restructures the original LIGO code for improved reproducibility, as a homework assignment for the [Fall 2025 installment of UC Berkeley's Stat 159/259 course, _Reproducible and Collaborative Data Science](https://ucb-stat-159-f25.github.io/site/). Authorship of the original analysis code rests with the LIGO collaboration._

The original LIGO notebook (LOSC_Event_tutorial.ipynb) was written using an old version of the scipy package and produces an error. For this homework, the code has been updated to use the modern syntax in order for it to run. Under the Matched filtering to find the signal section at codeblock 18, the code:
try: dwindow = signal.tukey(template.size, alpha=1./8) 
except: dwindow = signal.blackman(template.size)       
Is replaced by:
from scipy.signal import windows as win
try:
    dwindow = win.tukey(template.size, alpha=1/8)
except Exception:
    dwindow = win.blackman(template.size)
