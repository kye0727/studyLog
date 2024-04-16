# ML 성능 평가 지표(ML Evaluation Metric)
## 참고(Reference)
- 머신러닝 완벽 가이드(저자 권철민)
- [Classification Metrics(분류 모델 지표 ) 알아보기](https://only-wanna.tistory.com/entry/Classification-Metrics%EB%B6%84%EB%A5%98-%EB%AA%A8%EB%8D%B8-%EC%A7%80%ED%91%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0-TPR-FPR%EA%B3%BC-ROC-Curve-%EC%82%AC%EC%9D%B4-%EA%B4%80%EA%B3%84-%EB%B0%8F-AUC)
## 분류(Classification)
### 오차행렬(Confusion Matrix)
<table>
    <tr>
        <td></td>
        <td></td>
        <th scope="col" colspan="2">예측 클래스(Predicted Class)</th>
    </tr>
    <tr>
        <th></th>
        <th></th>
        <th>Negative(0)</th>
        <th>Positive(1)</th>
    </tr>
    <tr>
        <th rowspan="2">실제 클래스(Actual Class)</th>
        <th>Negative(0)</th>
        <td>TN(True Negative)</td>
        <td>FP(False Positive)</td>
    </tr>
    <tr>
        <th>Positive(0)</th>
        <td>FN(False Negative)</td>
        <td>TP(True Positive)</td>
    </tr>
</table>

오차행렬을 통해 정확도, 정밀도, 재현율을 정의할 수 있다.
### 정확도(Accuracy)
$$
정확도(Accuracy)
=\frac{결과가동일한예측데이터}{모든예측데이터}=\frac{TN+TP}{TN+FP+FN+TP}
$$
- 직관적인 모델 성능평가 지표이다.
- 불균형한 레이블 데이터 세트에서는 왜곡 가능성이 있다.
### 정밀도(Precision)
$$
정밀도(Precision)=\frac{TP}{FP+TP}
$$
- FP를 줄여 정밀도가 1에 가까워지는 것을 목표로 한다.
- Positive의 예측 성능을 더욱 정밀하게 측정하기 위한 평가 지표이다.
- 실제 음성 데이터를 양성으로 판단하면 안되는 경우에 중요하다.
### 재현율(Recall)
$$
재현율(Recall)=\frac{TP}{FN+TP}
$$
- FN을 줄여 실제 양성인 클래스를 음성으로 잘못 예측하는 것을 줄이는 것을 목표로 한다.
- 민감도(Sensitivity) 또는 TPR(True Positive Rate)라고 불린다.
- 실제 양성 데이터를 음성으로 판단하면 안되는 경우에 중요하다.
> **정밀도/재현율 트레이드오프(Trade-off)**   
정밀도와 재현율은 상호 보완관계이다.  
정밀도 $\darr$ => 재현율 $\uarr$ / 정밀도 $\uarr$ => 재현율 $\darr$
### F1 스코어
$$
F1=\frac{2}{\frac{1}{재현율(Recall)}+\frac{1}{정밀도(Precision)}}
$$
- 정밀도와 재현율이 어느 한쪽으로 치우치지 않았을때 높은 값을 가진다.
### ROC곡선(Receiver Operation Characteristic Curve) & AUC(Area Under Curve)
#### ROC곡선
ROC곡선은 FPR(False Positive Rate)의 변화에 따른 TPR(True Positive Rate)의 변화를 나타내는 곡선이다.  
- FPR은 음성을 양성으로 잘못 나타낸 수준을 나타내는 수치이다.
- TPR은 양성을 정확하게 예측한 수준을 나타내는 수치이다.  
- $FPR=\frac{FP}{(FP+TN)}$ / $TPR=\frac{TP}{(FN+TP)}$
#### AUC(Area Under Curve)
AUC는 ROC곡선 밑의 면적을 구한 것이다. 
- 1에 가까울수록 좋은 수치이다.
- AUC수치가 커지기 위해서는 FPR이 작은 상태에서 얼마나 큰 TPR을 얻을 수 있는지가 중요하다.
