why do you use unreal engine

- 작업 방식
- 블루프린트 비주얼 스크립팅 (노드 기반 에디터)
- 다른 엔진에 비해 제대로 된 시각 효과를 내기 쉬움

[The BEST way of learning 2D with UNREAL ENGINE 5 (youtube.com)](https://www.youtube.com/watch?v=IArNheV_W2A&list=PLEHVxFO1I6ekaCoG3JBR4m3qbhOpPO7V8&index=6)

## Start Project

Unreal Engine > GAMES > Third Person (보통은 blank로 하지만 익숙해지기 전까지는 이걸로) >

Project Default
- Target Platform: Desktop
- Quality preset: Scalable (컴퓨터 성능이 좋지 않은 경우)

---

## 2D Project settings

- `anti-aliasing`
    - 각진 선을 제거해 부드럽게 만들어 주는 기술
    - set Default Settings to Fast Approximate Anti Aliasing (FXAA)
    - still have problem → None
- `Motion Blur`
    - set this to False
- `Auto Exposure`
    - set this to False

**If black dot appears in the game**
- Project Settings > Maps and Modes > Default Pawn Class > None

**If the exposure is too bright**
- Camera > Exposure > Metering Mode > Manual / Exposure Compensation(노출 보정) > 10~11 (10.2)

---

## **free 2D assets**

need to check the lisence before using
(CC0의 경우 자유롭게 사용 가능)

- [itch.io](http://itch.io)
- [OpenGameAre.org](https://opengameart.org/)
- [Unity Asset Store](https://assetstore.unity.com/) (사용을 위해 몇 가지 과정을 거쳐야 함)
- UE Marketplace

---

## **Sprites**

이미지를 contents 파일에 넣고 해당 과정을 거쳐야 함
- rigth click > TEXTURE ACTION > Sprites Action > Apply Paper 2D Texture Settings

이미지를 더블 클릭하면 조금 더 세부적인 설정 가능
- texture filter

**이미지를 사용하기 위해서는 sprite로 바꿔줘야 함** (sprite는 맵에 drag in 가능, 이미지는 안 됨)
- right click > TEXTURE ACTION > Sprites Action > Create Sprite

**Sprite Settings**
여러 요소에 한번에 설정 적용 (select multiple sprite > right click > Asset Action > Edit selection in property matrix)

Change default import setting (Edit > Project Settings > Editor > Paper 2D - import)
- Pixels per unit: unreal engine unit 상에서 pixel의 크기를 정함 (보통은 0.25를 많이 씀 = 4)
    - 1 unit = 1 centimeter
    - character movement component를 사용할 때 굉장히 중요함 (캐릭터가 너무 작으면 적용할 때 그가 일어날 수도 있음)
- Pivot mode: sprite의 중심점을 정함

---

## Sprite Sheets

E**xtract sprite sheets**
1. right click sprite sheet > Sprite Action > Apply Paper 2D Texture Settings
2. right click sprite sheet > Sprite Action > Extract Sprites (sprite sheet의 추출을 도와줌)

**직접 영역 나누기**
1. Sprite Extract Mode > Grid
2. Set Cell Width/Height (제작자가 잘 설정해놨다면 주어진 길이에서 열과 행에 있는 요소의 수만큼 각각 나누면 됨)
3. 다 끝났다면 click Extract

- 만약 제작자의 실수로 밑부분에 1 pixel gap이 있다면?
    1. Spacing Y를 1로 설정함 (1 pixel의 gap이 생김)
    2. Cell Height를 1 줄여줌 (간격 맞추기)

**Create Flipbook**
- Select multiple sprite > right click > Create Flipbook

---

## Asset Naming

[Recommended Asset Naming Conventions in Unreal Engine projects | Unreal Engine 5.2 Documentation](https://docs.unrealengine.com/5.2/en-US/recommended-asset-naming-conventions-in-unreal-engine-projects/)

`[AssetTypePrefix]_[AssetName]_[Descriptor]_[OptionalVariantLetterOrNumber]`
- `AssetTypePrefix` identifies the type of Asset, refer to the table below for details.
- `AssetName` is the Asset's name.
- `Descriptor` provides additional context for the Asset, to help identify how it is used. For example, whether a texture is a normal map or an opacity map.
- `OptionalVariantLetterOrNumber` is optionally used to differentiate between multiple versions or variations of an asset.

---

## Normal Map

tutorial : [https://youtu.be/vIBW0j7JDRQ?si=zQEmVq4SYdlpg6e6](https://youtu.be/vIBW0j7JDRQ?si=zQEmVq4SYdlpg6e6)

Edge Normals Script : [https://github.com/securas/EdgeNormals](https://github.com/securas/EdgeNormals)

1. Aseprite → oepn sprite sheet → (file>scripts>edge_normal) → apply and download
2. change the name of the sprite sheet like below

![[Pasted image 20250724111416.png]]

default sprite sheet : _d

edge normal sprite sheet : _n

3. In unreal engine → All → Plugins → Paper2DContents → copty DefaultLitSpriteMaterial to your contents → change its name to M_CustomLitPaperMaterial
4. 
![[Pasted image 20250724111442.png]]

5. right click → Create Material Instance → name it MI_CustomLitPaperMaterial
6. Click default sprite sheet → Sprite Action → Apply Paper2D Texture Settings
7. Extract Sprite (It will automatically apply edge noraml sprite sheet)
8. Change the Default Material of the Sprite to MI_CustomLitPaperMaterial

before
![[Pasted image 20250724111547.png]]

after
![[Pasted image 20250724111609.png]]

---

## Attach Camera to the Character

---

## Blueprint

- 2D 배경과 물체가 자꾸 겹친다면?
    → oepn blueprint > Sprite > Translucency Sort Priority
    
    숫자가 클수록 앞에 있음