# Stable Diffusion Inpainting with SAM
<br>

## Stable Diffusion Inpainting
<img width="1107" height="407" alt="image (6)" src="https://github.com/user-attachments/assets/39f72ddf-7eab-44a5-beba-dfa5a68e7e29" />

- Stable Diffusion Inpainting 모델은 Diffusion 모델을 활용한 이미지 복원 및 편집 기술로, 손상된 이미지의 복구 또는 특정 영역을 원하는 스타일이나 콘텐츠로 대체하는 작업을 수행
- 사용자가 지정한 영역과 텍스트 프롬프트를 바탕으로 해당 영역의 콘텐츠를 생성

<br>





## Segment Anything Model(SAM)
<img width="1091" height="435" alt="image" src="https://github.com/user-attachments/assets/3d6bae47-d471-45b3-89b5-6e5b307749e6" />

- SAM은 메타(Meta)에서 개발한 이미지 세분화 모델로, 다양한 이미지 세분화 작업을 수행
- SAM 모델을 사용하여 원하는 객체를 포인트로 지정해 입력 포인트에 대해 객체를 자동으로 분할


<br>




## Masks
<img width="1072" height="347" alt="image" src="https://github.com/user-attachments/assets/06b9122b-e22e-4d0f-9478-af9eee4cadcc" />

- 객체를 SAM 모델을 통해 세분화를 진행
- 세분화 결과, score를 확인하여 객체를 가장 잘 세분화한 mask를 지정

<br>
<img width="922" height="367" alt="image" src="https://github.com/user-attachments/assets/0eacee0c-c31c-4e54-a3eb-1efdd6d86cd9" />

- 가장 높은 점수를 가진 mask에 대해 경계선에서의 영역을 확장
- mask를 확장하여 inpaint시에 경계 부분을 포함하거나 모델이 놓친 영역을 보완하여 더 자연스러운 결과를 얻을 수 있게 함

<br>




## Inpainting
<img width="2048" height="512" alt="다운로드 (3) (1)" src="https://github.com/user-attachments/assets/802e255d-dbd1-4df0-a4fb-3edd61950cb9" />

- SAM을 통해 Segment한 객체에 대해 Stable Diffusion Inpainting 모델을 사용하여 Inpainting 진행
- 프롬프트 입력 -> "Chocolate donuts topped with sprinkles."

<br>





## Gradio Serving
<img width="1280" src="https://github.com/user-attachments/assets/cee1204d-b0e9-4c8c-b452-ae41108484d1" />

- 원본 이미지와 SAM을 통해 얻은 mask 이미지를 삽입 
- 사용자의 프롬프트 입력과 Guidance Scale, Number of Samples에 따른 갯수 설정 가능
- Guidance Scale : 모델이 프롬프트에 얼마나 강하게 의존할지를 결정
- Number of Samples : 프롬프트를 기반으로 몇개의 이미지를 생성할지를 결정
- 프롬프트를 "A complete macaron with a colorful pattern on a plate."로 입력한 뒤 Guidance Scale은 10, Number of Samples는 2로 설정하여 실행
