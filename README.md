# SMPS

전체적인 동작은 PWM IC인 TNY279PN의 PWM 발진신호로 초퍼 트랜스를 구동하여 2차측에 전달해 +5V,-5V,+40V가 출력되는 구성입니다. 아울러 안정적인 정전압을 유지하기 위한 피드백 신호는 포토커플러를 사용하여 구현하였습니다.


# 제작한 SMPS 및 PCB 

![./result.jpg](./1.jpg)
![image](https://github.com/jinhoheoo/SMPS/assets/153490852/d1748533-69fa-4812-b305-584416baee55)
![image](https://github.com/jinhoheoo/SMPS/assets/153490852/f8c0981d-5c2f-426d-82c9-d54d7ddf9a5c)


# SMPS 동작 영상

https://youtube.com/shorts/sAFXUCncAM8

# 세부사항 및 포트폴리오


![image](https://github.com/jinhoheoo/SMPS/assets/153490852/d05125e2-eac5-4da4-be80-1ce280ccb0e9)

![image](https://github.com/jinhoheoo/SMPS/assets/153490852/370092da-d5f7-4be6-b61b-524f4f5d29df)

![image](https://github.com/jinhoheoo/SMPS/assets/153490852/bd05c39d-a4fa-48d6-b977-5fb2b7b6e834)

-동작원리

1. 교류(AC85V ∼ 265V)나 직류(DC80V ∼ 240V) 전압이 인가되면 바리스타로 서지를 막아주고 퓨즈와 서미스터(NTC)는 돌입전류에 의해서 콘덴서 C6가 소손 되는 것을 막아줍니다.
입력신호는 브릿지 다이오드를 거쳐 정류된 후 파이필터에 의해 평활되고 노이즈가 제거 되어 직류 전압이 됩니다.

2. TNY279 내부의 MOSFET이 132KHz로 스위칭 하는 펄스에 따라서 MOSFET가 ON/OFF 스위칭 동작을 하는데 이 때 FET가 ON시 트랜스의 1차측 권선에 전류가 흘러 에너지가 축적되고 FET가 OFF 될 시 축척된 에너지가 2차측 권선으로 출력됩니다. 트랜스와 병렬로 스너버 회로를 연결하여 트랜스로 인한 누설 인덕턴스가 FET의 스위칭에 의해 발생하는 서지를 스너버 회로로 막아줍니다.

3. MOSFET OFF상태일 때 2차로 넘어온 전압은 다이오드를 지나 정류되고 파이필터를 거쳐 평활되어 직류 전압(+40V, +5V, -5V)을 얻습니다. 이때  5V에 다이오드와 병렬연결 된 스너버 회로(다이오드 효율 개선용)는 다이오드 trr(역방향 회복 시간)을  짧게 줄여주는 역할과 ON/OFF시 발생되는 노이즈를 제거해줍니다. MOSFET ON 상태가 되면 2차측에 전압이 넘어오지 않아 파이필터의 C에 저장된 전압이 방전하여 전압을 유지시킵니다.

4. 안정적인 전압을 얻기 위해 포토커플러를 이용해 피드백 제어를 합니다. TNY279의 EN(UV)핀은 HIGH상태 일 때 정상동작하여 2차측 포토커플러의 LED가 OFF 상태여야 합니다. 그러나 출력의 전압이 증가하여 TL431의 REF단자에 들어오는 전압이 증가하면 K단으로 흘러들어오는 전류 즉 포토커플러에 흐르는 전류가 증가하여 ON되어 TR로 전달됩니다. TR이 ON이 되면 TNY279의 EN(UV)핀이 0.2V로 낮아져 LOW상태가 되므로 동작을 중지합니다.

5. 이 상태가 유지되어 2차측 전압이 감소하여 LED로 가는 전류가 감소하고  OFF가 됩니다. 그러면 EN(UV)핀이 다시 HIGH가 되고 TNY279가 다시 정상적인 작동을 하게 되어 FET가 ON/OFF 스위칭으로 안정적인 전압을 얻습니다.


![image](https://github.com/jinhoheoo/SMPS/assets/153490852/eaefd9d5-5a04-4ba1-b012-366cded46aca)
![image](https://github.com/jinhoheoo/SMPS/assets/153490852/c8c41eae-2521-427e-af90-43c8e175160d)

![image](https://github.com/jinhoheoo/SMPS/assets/153490852/25c7f08f-c440-4f16-b0e9-0dbae596ffbe)
![image](https://github.com/jinhoheoo/SMPS/assets/153490852/ee561783-e869-4f5c-90e7-eb80cb6ba941)
![image](https://github.com/jinhoheoo/SMPS/assets/153490852/8b4f7456-fa9e-4da9-8e74-1a9f2628ac46)



