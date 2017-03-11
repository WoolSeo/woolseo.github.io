#Matplotlib로 그래프 그리기
그래프를 그리는 비싼 프로그램들도 많다. 하지만 우린 돈이 없다. 그렇다고 그냥 엑셀로 그리면 품위가 떨어진다. 우린 다행히 아주 조금 코딩을 할 수 있다.
최근에 나는 학생들이 활용할 수 있는 다양한 그래프를 그리기 위한 프로그램들을 사용해봤다.
- Gnuplot http://www.gnuplot.info/
- Processing https://www.processing.org/
- Python Matplotlib http://matplotlib.org/ 

셋 다 대부분의 OS를 지원한다. Windows, Mac, linux까지 지원한다.
여러가지 이유가 있지만 난 **Matplotlib**을 사용하려 한다.
파이썬이 처음이라고? 그래도 괜찮다. 아주 간단하다.

##Python IDE 설치
Matplotlib는 파이썬의 라이브러리이다. 사용하려면 당연히 파이썬을 설치해야 한다.
아주 하드하게 파이썬만 깔고 텍스트에디터에서 코딩해 저장한 다음 콘솔에서 실행할 수 있다.
하지만 난 IDE를 사용할 것을 추천한다. 여러모로 실행까지 편하다. 내가 사용해 본 IDE는 2개다.
- Anaconda https://www.continuum.io/downloads
- Canopy https://www.enthought.com/products/canopy/

두 개 중 하나를 받아 설치하자. 사용법은 DEV C++이나 Code block과 거의 비슷하다.

여기서 난 Canopy를 사용했다.
참고로 파이썬이 궁금하다면? https://wikidocs.net/book/1

##점으로 그래프 그리기
- 점의 좌표를 입력해서 그 점들을 잇는 가장 간단한 직선 그래프를 그려보자.

<pre>
import matplotlib.pyplot as plt

plt.plot([0,60],[0,73])
plt.xlabel('t[s]')
plt.ylabel('x[m]')
plt.show()
</pre>

<img src=./images/matplot1_a.png width=400px>


(0,0)과 (60,73) 두 점을 잇는 직선이다. 쉽다.
`import`는 라이브러리를 불러온다.


- 점 세 개를 연결해보자.

<pre>
import matplotlib.pyplot as plt

plt.plot([0,60,84],[0,73.2,146.4])
plt.xlabel('t[s]')
plt.ylabel('x[m]')
plt.show()
</pre>

<img src=./images/matplot1_b.png width=400px>

(0,0)과 (60,73.2), (84, 146.4) 세 점을 연결했다.


- 또 다른 직선을 하나 추가해보자.

<pre>
import matplotlib.pyplot as plt

plt.plot([0,60,84],[0,73.2,146.4])
plt.plot([0,84],[0,146.4])
plt.xlabel('t[s]')
plt.ylabel('x[m]')
plt.show()
</pre>

<img src=./images/matplot1_c.png width=400px>


- 마지막으로 x축과 y축의 범위를 `plt.axis`로 설정할 수 있다.
그리고 간단히 연산도 시킬 수 있다.

<pre>
import matplotlib.pyplot as plt

plt.axis([0,130,0,300])
plt.plot([0,60,120],[0,1.22*60,3.05*60+1.22*60])
plt.plot([0,120],[0,3.05*60+1.22*60])
plt.xlabel('t[s]')
plt.ylabel('x[m]')
plt.show()
</pre>

<img src=./images/matplot1_d.png width=400px>


##함수 그래프 그리기
- 임의의 수식을 그래프로 나타내야 할 때가 많다. 함수를 그리는 것도 간단하다. 함수를 정의하고 사용하면 된다.

<pre>
import numpy as np
import matplotlib.pyplot as plt

t = np.arange(0.,10.,0.01)
x = np.sin(t)

plt.axis([0,10,-1.5,1.5])
plt.plot(t,x,linewidth=2.)
plt.xlabel('t[s]')
plt.ylabel('x[m]')
plt.show()
</pre>

<img src=./images/matplot2_a.png width=400px>


가로 축에 사용할 t의 범위를 `arrange`를 이용해 정의했다. 0에서부터 10까지 0.01 간격으로 배열을 만들었다. 세로 축인 x는 t에 대한 사인함수이다. `plot`에서 `linewidth`를 통해 선의 굵기를 설정했다.


- 다른 함수를 하나 그려보자.

<pre>
import numpy as np
import matplotlib.pyplot as plt

t = np.arange(0.,4.,0.01)
x = 3*t - 4 * t**2 + t**3

plt.axis([0,5,-5,15])
plt.plot(t,x,linewidth=2.)
plt.plot([2,4],[-2,12],color='black',linestyle='dashed')
plt.scatter([2,4],[-2,12],color='black')
plt.xlabel('t[s]')
plt.ylabel('x[m]')
plt.show()
</pre>

<img src=./images/matplot2_b.png width=400px>

파이썬에서 거듭제곱은 `**`이다. `scatter`는 점을 찍어준다.
