# 재정정보 AI 검색 알고리즘 프로젝트

## 프로젝트 소개

해당 프로젝트는 Dacon에서 진행한 재정정보 AI 검색 알고리즘 경진대회로서,
열린재정의 중앙정부 재정 정보 검색 및 제공 편의성과 활용도를 높이는 질의 응답 AI알고리즘 개발이 목적입니다.
 [Dacon 대회](https://dacon.io/competitions/official/236295/overview/description)

## 사용환경
개인 GPU가 아닌 Kaggle에서 제공한 *T4 x2* 이기 때문에 *Jupyter notebook*으로 작성되었습니다.

## 설명

이미지

## 사용방법
먼저 대회 링크에서 데이터를 다운받고, kaggle에서는 한글이름을 가진 파일들을 사용할 수 없기 때문에 이를 숫자로 바꾸어 줍니다.
<details>
<summary>코드</summary>

```python
test_source = [
    "「FIS 이슈 & 포커스」 22-4호 《중앙-지방 간 재정조정제도》",
    "「FIS 이슈 & 포커스」 23-2호 《핵심재정사업 성과관리》",
    "「FIS 이슈 & 포커스」(신규) 통권 제1호 《우발부채》",
    "「FIS 이슈&포커스」 22-2호 《재정성과관리제도》",
    "국토교통부_행복주택출자",
    "보건복지부_노인장기요양보험 사업운영",
    "보건복지부_부모급여(영아수당) 지원",
    "산업통상자원부_에너지바우처",
    "중소벤처기업부_혁신창업사업화자금(융자)"
]

train_source = [
    "「FIS 이슈 & 포커스」 22-3호 《재정융자사업》",
    "「FIS 이슈 & 포커스」 23-3호 《조세지출 연계관리》",
    "1-1 2024 주요 재정통계 1권",
    "2024 나라살림 예산개요",
    "2024년도 성과계획서(총괄편)",
    "고용노동부_내일배움카드(일반)",
    "고용노동부_조기재취업수당",
    "고용노동부_청년일자리창출지원",
    "국토교통부_민간임대(융자)",
    "국토교통부_소규모주택정비사업",
    "국토교통부_전세임대(융자)",
    "보건복지부_노인일자리 및 사회활동지원",
    "보건복지부_생계급여",
    "월간 나라재정 2023년 12월호",
    "재정통계해설",
    "중소벤처기업부_창업사업화지원"
]
# 두 리스트를 합칩니다
all_sources = test_source + train_source

# 딕셔너리를 생성합니다
h2n = {name : str(idx) for idx, name in enumerate(all_sources)}
n2h = {str(idx) : name for idx, name in enumerate(all_sources)}

for i in range(len(all_sources)):
    print(i,n2h[str(i)])
```
</details>

그 후 코드에서 수정할 곳은
`class Opt:`
으로 시작하는 Block인데, 모델주소는 직접 허깅페이스 주소를입력해도 되고, 다운받은뒤 로컬주소를 작성해도 무방합니다.

`self.hf_token`과 `wandb.login(key='')`는 필요시 직접 입력해주셔야합니다. 
`rerank`와 `single_passage`는 각각 *rerank*와 *single_passage*적용 여부이며(*True or False*), `train`과 `peft`는 각각 파인튜닝학습 과 그학습된 모델로 추론 여부 입니다.
중간에 *OOM*이슈가 뜬다면 
```python
!for pid in $(lsof /dev/nvidia* | awk '{print $2}' | tail -n +2); do kill -9 $pid; done
```
코드를 사용해 환경을 유지시키며 변수및 GPU memory를 초기화하면 됩니다.
