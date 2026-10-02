[index.html](https://github.com/user-attachments/files/32956134/index.html)
# cuddly-adventure<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
  <title>새창원청년회의소 회원수첩 및 정관 통합본</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body { font-family: 'Inter', 'Noto Sans KR', sans-serif; background-color: #f3f4f6; -webkit-tap-highlight-color: transparent; }
    .app-container { max-width: 480px; margin: 0 auto; background-color: #ffffff; min-height: 100vh; position: relative; box-shadow: 0 0 20px rgba(0,0,0,0.05); overflow-x: hidden; }
    .scroll-hide::-webkit-scrollbar { display: none; }
    .scroll-hide { -ms-overflow-style: none; scrollbar-width: none; }
    
    table { width: 100%; border-collapse: collapse; margin-top: 15px; margin-bottom: 25px; font-size: 12px; background-color: white; border: 1px solid #e5e7eb; }
    th, td { border: 1px solid #e5e7eb; padding: 10px 8px; text-align: center; vertical-align: middle; word-break: keep-all; }
    th { background-color: #f8fafc; color: #1e3a8a; font-weight: 800; }
    
    .toast { position: fixed; bottom: -100px; left: 50%; transform: translateX(-50%); background-color: #1f2937; color: white; padding: 14px 24px; border-radius: 9999px; font-size: 14px; font-weight: bold; transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1); z-index: 9999; white-space: nowrap; box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1); }
    .toast.show { bottom: 40px; }
    
    .rules-content p { margin-bottom: 0.75rem; color: #374151; line-height: 1.6; }
    .rules-content .doc-title { text-align: center; font-size: 20px; font-weight: 900; color: #1e3a8a; margin-top: 2.5rem; margin-bottom: 1.5rem; border-bottom: 2px solid #1e3a8a; padding-bottom: 0.5rem; }
    .rules-content h3 { margin-top: 2rem; margin-bottom: 1rem; font-size: 16px; font-weight: 900; color: #ffffff; background-color: #1e3a8a; padding: 8px 12px; border-radius: 6px; box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
    .rules-content h4 { margin-top: 1.5rem; margin-bottom: 0.75rem; font-weight: 800; color: #1e3a8a; border-left: 4px solid #1e3a8a; padding-left: 8px; font-size: 15px; }
  </style>
</head>
<body class="bg-gray-100">
  <div id="app" class="app-container flex flex-col"></div>
  <div id="toast" class="toast"></div>

  <script>
    const defaultRegular = [
      { id: 'r1', name: '김용국', phone: '010-7997-1485', role: '상임부회장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r2', name: '김대훈', phone: '010-4444-7012', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r3', name: '박동현', phone: '010-3168-2555', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r4', name: '최정원', phone: '010-9331-7887', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r5', name: '박찬', phone: '010-8525-3594', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r6', name: '김동수', phone: '010-6665-6025', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r7', name: '백석영', phone: '010-9398-8858', role: '제43대 회장', company: '', joinYear: '2023', imgUrl: '' },
      { id: 'r8', name: '김민재', phone: '010-9947-4856', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r9', name: '박희열', phone: '010-8008-8679', role: '제44대 회장', company: '', joinYear: '2024', imgUrl: '' },
      { id: 'r10', name: '김민효', phone: '010-9343-6691', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r11', name: '박인욱', phone: '010-3525-6946', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r12', name: '하재우', phone: '010-5845-8300', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r13', name: '이상욱', phone: '010-8821-6166', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r14', name: '정승화', phone: '010-8859-4633', role: '제45대 회장/직전회장', company: '', joinYear: '2025', imgUrl: '' },
      { id: 'r15', name: '최주연', phone: '010-7709-8229', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r16', name: '김선혁', phone: '010-5223-8675', role: '특우회.부인회 담당분과위원', company: '', joinYear: '', imgUrl: '' },
      { id: 'r17', name: '이동준', phone: '010-3452-7177', role: '연수이사', company: '', joinYear: '', imgUrl: '' },
      { id: 'r18', name: '안재현', phone: '010-9791-9994', role: '회원확충분과위원장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r19', name: '전성복', phone: '010-8876-9275', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r20', name: '하주은', phone: '010-8009-6560', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r21', name: '이현승', phone: '010-5265-1062', role: '회장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r22', name: '정성원', phone: '010-6724-1137', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r23', name: '이지원', phone: '010-2033-0063', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r24', name: '선진호', phone: '010-5663-8234', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r25', name: '조무성', phone: '010-9334-8816', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r26', name: '황준호', phone: '010-3534-5523', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r27', name: '김우진', phone: '010-3842-1282', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r28', name: '최재원', phone: '010-6269-7296', role: '총무이사', company: '', joinYear: '', imgUrl: '' },
      { id: 'r29', name: '주상훈', phone: '010-8552-8912', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r30', name: '이준호', phone: '010-8878-7907', role: '기록포상분과위원장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r31', name: '정광양', phone: '010-9268-5848', role: '내무부회장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r32', name: '권아경', phone: '010-5560-5542', role: '감사', company: '', joinYear: '', imgUrl: '' },
      { id: 'r33', name: '안병주', phone: '010-6633-8141', role: '외무부회장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r34', name: '최윤영', phone: '010-7156-2524', role: '감사', company: '', joinYear: '', imgUrl: '' },
      { id: 'r35', name: '최광연', phone: '010-9336-6043', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r36', name: '이민성', phone: '010-6330-1658', role: '기획/재정이사', company: '', joinYear: '', imgUrl: '' },
      { id: 'r37', name: '김인범', phone: '010-6606-4729', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r38', name: '김성빈', phone: '010-4175-7558', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r39', name: '김경원', phone: '010-4779-6760', role: '국제활동분과위원장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r40', name: '이원준', phone: '010-5560-7798', role: '사무국장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r41', name: '정준혁', phone: '010-8643-7993', role: '청소년활동분과위원장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r42', name: '전민진', phone: '010-4768-7134', role: '지도력개발분과위원장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r43', name: '한충건', phone: '010-6738-0317', role: '체육우호분과위원장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r44', name: '윤성환', phone: '010-8989-7743', role: '지역홍보분과위원장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r45', name: '정재민', phone: '010-4866-4569', role: '의전이사', company: '', joinYear: '', imgUrl: '' },
      { id: 'r46', name: '한희승', phone: '010-9147-2448', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r47', name: '심호성', phone: '010-2504-1378', role: '사무차장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r48', name: '이종진', phone: '010-3349-1284', role: '사무차장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r49', name: '이태검', phone: '010-9555-2887', role: '사무차장', company: '', joinYear: '', imgUrl: '' },
      { id: 'r50', name: '황영민', phone: '010-9891-5577', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r51', name: '하태현', phone: '010-3104-7221', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r52', name: '김원욱', phone: '010-4935-5757', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r53', name: '장흠희', phone: '010-7547-1032', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r54', name: '박수민', phone: '010-5262-4335', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r55', name: '하지웅', phone: '010-3425-2623', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r56', name: '김정헌', phone: '010-4947-8287', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r57', name: '박세은', phone: '010-4433-3320', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r58', name: '원대연', phone: '010-9258-0010', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r59', name: '공현준', phone: '010-9865-5553', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r60', name: '김지환', phone: '010-5494-5583', role: '', company: '', joinYear: '', imgUrl: '' },
      { id: 'r61', name: '이승준', phone: '010-9795-5458', role: '', company: '', joinYear: '', imgUrl: '' }
    ];

    const defaultSpecial = [
      { id: 's1', name: '이종화', phone: '010-3836-2557', role: '', company: '제일농약사료 대표', imgUrl: '' },
      { id: 's2', name: '이종만', phone: '010-5596-1090', role: '', company: '자영업', imgUrl: '' },
      { id: 's3', name: '황규윤', phone: '010-3567-4747', role: '', company: '자영업', imgUrl: '' },
      { id: 's4', name: '김정수', phone: '010-4655-4245', role: '', company: '자영업', imgUrl: '' },
      { id: 's5', name: '박철용', phone: '010-6574-2695', role: '', company: '주남농장 대표', imgUrl: '' },
      { id: 's6', name: '강래수', phone: '010-4871-1008', role: '', company: '부산경남우유협동조합 조합장 / 푸른목장 대표', imgUrl: '' },
      { id: 's7', name: '김병섭', phone: '010-3568-8899', role: '', company: '나르미특장차 영남지역 영업지원실 실장', imgUrl: '' },
      { id: 's8', name: '이판우', phone: '010-9485-6567', role: '', company: '자영업', imgUrl: '' },
      { id: 's9', name: '박창식', phone: '010-3567-3845', role: '', company: '청와축산 대표/㈜제이피앤케이 대표', imgUrl: '' },
      { id: 's10', name: '김민재', phone: '010-3866-6870', role: '', company: '무량사 회주 지성, 납골당 대표', imgUrl: '' },
      { id: 's11', name: '박치근', phone: '010-9330-3304', role: '', company: '㈜레알개발 대표이사', imgUrl: '' },
      { id: 's12', name: '황진용', phone: '010-3864-7111', role: '', company: '경남관광재단 관광마케팅 본부장', imgUrl: '' },
      { id: 's13', name: '한경수', phone: '010-4582-5440', role: '', company: '동창원직업소개소 대표', imgUrl: '' },
      { id: 's14', name: '허상회', phone: '010-8673-2388', role: '', company: '시민금방 대표', imgUrl: '' },
      { id: 's15', name: '정철식', phone: '010-6590-1485', role: '', company: '자영업', imgUrl: '' },
      { id: 's16', name: '이무식', phone: '010-4020-0090', role: '', company: '화천산업 대표', imgUrl: '' },
      { id: 's17', name: '이상석', phone: '010-3567-8227', role: '', company: '가월농원 대표', imgUrl: '' },
      { id: 's18', name: '김삼모', phone: '010-3598-4464', role: '', company: '㈜ SMK 회장', imgUrl: '' },
      { id: 's19', name: '유재준', phone: '010-8507-5409', role: '', company: '', imgUrl: '' },
      { id: 's20', name: '신종두', phone: '010-4844-0402', role: '', company: '자영업', imgUrl: '' },
      { id: 's21', name: '서종근', phone: '010-3586-8998', role: '', company: '광원산업(주) 대표이사', imgUrl: '' },
      { id: 's22', name: '박정서', phone: '010-3559-7417', role: '', company: '', imgUrl: '' },
      { id: 's23', name: '김경수', phone: '010-3889-4546', role: '', company: '㈜태송 대표이사', imgUrl: '' },
      { id: 's24', name: '정주영', phone: '010-7302-0770', role: '', company: '', imgUrl: '' },
      { id: 's25', name: '오진석', phone: '010-3860-3189', role: '', company: '㈜태평양항공여행사', imgUrl: '' },
      { id: 's26', name: '조기영', phone: '010-4561-0936', role: '', company: '', imgUrl: '' },
      { id: 's27', name: '강병수', phone: '010-3581-7102', role: '', company: '', imgUrl: '' },
      { id: 's28', name: '주창욱', phone: '010-9327-4315', role: '', company: '자영업', imgUrl: '' },
      { id: 's29', name: '최정문', phone: '010-3559-3577', role: '', company: '정엔지니어링 대표', imgUrl: '' },
      { id: 's30', name: '이용기', phone: '010-4511-2676', role: '부회장', company: '한마음노무법인 창원사무소 실장', imgUrl: '' },
      { id: 's31', name: '김호섭', phone: '010-4166-0212', role: '부회장', company: '', imgUrl: '' },
      { id: 's32', name: '정상철', phone: '010-4696-8887', role: '직전회장 / 경남지구JC 특우회 부회장', company: '㈜동명 대표, ㈜계명목재 대표', imgUrl: '' },
      { id: 's33', name: '김성훈', phone: '010-2587-8159', role: '', company: '', imgUrl: '' },
      { id: 's34', name: '박기종', phone: '010-3835-1376', role: '', company: '', imgUrl: '' },
      { id: 's35', name: '윤중원', phone: '010-4598-6061', role: '', company: '', imgUrl: '' },
      { id: 's36', name: '모상도', phone: '010-8474-0006', role: '', company: '대동애니콜 통신 대표', imgUrl: '' },
      { id: 's37', name: '김도한', phone: '010-9235-9988', role: '', company: '', imgUrl: '' },
      { id: 's38', name: '김병희', phone: '010-2352-8094', role: '', company: '', imgUrl: '' },
      { id: 's39', name: '이종환', phone: '010-6403-8000', role: '', company: '', imgUrl: '' },
      { id: 's40', name: '이영주', phone: '010-3843-4824', role: '회장', company: '회장', imgUrl: '' },
      { id: 's41', name: '박종석', phone: '010-4519-0919', role: '', company: '', imgUrl: '' },
      { id: 's42', name: '김동진', phone: '010-8293-3318', role: '감사', company: '', imgUrl: '' },
      { id: 's43', name: '박정훈', phone: '010-5532-2168', role: '사무국장', company: '', imgUrl: '' },
      { id: 's44', name: '우상범', phone: '010-8801-1873', role: '', company: '', imgUrl: '' },
      { id: 's45', name: '송성명', phone: '010-9144-5564', role: '', company: '다솜부동산개발 대표 / ㈜헤리티지글램핑장 대표', imgUrl: '' },
      { id: 's46', name: '최재영', phone: '010-4552-5991', role: '감사', company: '', imgUrl: '' },
      { id: 's47', name: '서미숙', phone: '010-3801-7942', role: '', company: '', imgUrl: '' },
      { id: 's48', name: '김용기', phone: '010-2549-0495', role: '', company: '', imgUrl: '' },
      { id: 's49', name: '신재훈', phone: '010-8778-2252', role: '', company: '', imgUrl: '' },
      { id: 's50', name: '박재효', phone: '010-2879-5807', role: '총무이사', company: '', imgUrl: '' },
      { id: 's51', name: '홍연기', phone: '010-8505-8461', role: '홍보이사', company: '한화에어로스페이스 부장', imgUrl: '' },
      { id: 's52', name: '이상석', phone: '010-2862-8445', role: '체육이사', company: '에스팜 대표 / 로하스메디 부산,경남 총괄지점장', imgUrl: '' },
      { id: 's53', name: '김정욱', phone: '010-9551-2473', role: '의전이사', company: '', imgUrl: '' },
      { id: 's54', name: '반광규', phone: '010-2102-3051', role: '', company: '', imgUrl: '' },
      { id: 's55', name: '김민수', phone: '010-6353-8899', role: '', company: '현대환경개발㈜ 대표이사', imgUrl: '' },
      { id: 's56', name: '장진수', phone: '010-9621-3588', role: '', company: '', imgUrl: '' },
      { id: 's57', name: '주형수', phone: '010-4911-6827', role: '', company: '주형수세무회계사무소 세무사', imgUrl: '' },
      { id: 's58', name: '남현민', phone: '010-4870-9279', role: '', company: '', imgUrl: '' },
      { id: 's59', name: '박중원', phone: '010-9400-5552', role: '', company: '', imgUrl: '' },
      { id: 's60', name: '정동진', phone: '010-9663-4858', role: '', company: '디자인스타 광고기획 대표', imgUrl: '' },
      { id: 's61', name: '이상민', phone: '010-6212-6791', role: '정회원담당이사', company: '', imgUrl: '' },
      { id: 's62', name: '신상영', phone: '010-4477-3379', role: '', company: '', imgUrl: '' },
      { id: 's63', name: '윤병철', phone: '010-4628-0220', role: '', company: '대운수출포장 대표', imgUrl: '' }
    ];

    const defaultPastLom = [
      { id: 's1', generation: 2, name: '이종화', phone: '010-3836-2557', company: '제일농약사료 대표', imgUrl: '' },
      { id: 's2', generation: 5, name: '이종만', phone: '010-5596-1090', company: '자영업', imgUrl: '' },
      { id: 's5', generation: 10, name: '박철용', phone: '010-6574-2695', company: '주남농장 대표', imgUrl: '' },
      { id: 's3', generation: 11, name: '황규윤', phone: '010-3567-4747', company: '자영업', imgUrl: '' },
      { id: 's6', generation: 14, name: '강래수', phone: '010-4871-1008', company: '부산경남우유협동조합 조합장 / 푸른목장 대표', imgUrl: '' },
      { id: 's10', generation: 16, name: '김민재', phone: '010-3866-6870', company: '무량사 회주 지성, 납골당 대표', imgUrl: '' },
      { id: 's11', generation: 17, name: '박치근', phone: '010-9330-3304', company: '㈜레알개발 대표이사', imgUrl: '' },
      { id: 's12', generation: 18, name: '황진용', phone: '010-3864-7111', company: '경남관광재단 관광마케팅 본부장', imgUrl: '' },
      { id: 's16', generation: 21, name: '이무식', phone: '010-4020-0090', company: '화천산업 대표', imgUrl: '' },
      { id: 's17', generation: 22, name: '이상석', phone: '010-3567-8227', company: '가월농원 대표', imgUrl: '' },
      { id: 's21', generation: 24, name: '서종근', phone: '010-3586-8998', company: '광원산업(주) 대표이사', imgUrl: '' },
      { id: 's18', generation: 25, name: '김삼모', phone: '010-3598-4464', company: '㈜ SMK 회장', imgUrl: '' },
      { id: 's20', generation: 26, name: '신종두', phone: '010-4844-0402', company: '자영업', imgUrl: '' },
      { id: 's25', generation: 27, name: '오진석', phone: '010-3860-3189', company: '㈜태평양항공여행사', imgUrl: '' },
      { id: 's23', generation: 28, name: '김경수', phone: '010-3889-4546', company: '㈜태송 대표이사', imgUrl: '' },
      { id: 's28', generation: 30, name: '주창욱', phone: '010-9327-4315', company: '자영업', imgUrl: '' },
      { id: 's29', generation: 32, name: '최정문', phone: '010-3559-3577', company: '정엔지니어링 대표', imgUrl: '' },
      { id: 's30', generation: 33, name: '이용기', phone: '010-4511-2676', company: '한마음노무법인 창원사무소 실장', imgUrl: '' },
      { id: 's36', generation: 34, name: '모상도', phone: '010-8474-0006', company: '대동애니콜 통신 대표', imgUrl: '' },
      { id: 's45', generation: 35, name: '송성명', phone: '010-9144-5564', company: '다솜부동산개발 대표 / ㈜헤리티지글램핑장 대표', imgUrl: '' },
      { id: 's55', generation: 37, name: '김민수', phone: '010-6353-8899', company: '현대환경개발㈜ 대표이사', imgUrl: '' },
      { id: 's57', generation: 38, name: '주형수', phone: '010-4911-6827', company: '주형수세무회계사무소 세무사', imgUrl: '' },
      { id: 's51', generation: 39, name: '홍연기', phone: '010-8505-8461', company: '한화에어로스페이스 부장', imgUrl: '' },
      { id: 's60', generation: 40, name: '정동진', phone: '010-9663-4858', company: '디자인스타 광고기획 대표', imgUrl: '' },
      { id: 's52', generation: 41, name: '이상석', phone: '010-2862-8445', company: '에스팜 대표 / 로하스메디 부산,경남 총괄지점장', imgUrl: '' },
      { id: 's63', generation: 42, name: '윤병철', phone: '010-4628-0220', company: '대운수출포장 대표', imgUrl: '' },
      { id: 'r7', generation: 43, name: '백석영', phone: '010-9398-8858', company: '', imgUrl: '' },
      { id: 'r9', generation: 44, name: '박희열', phone: '010-8008-8679', company: '', imgUrl: '' },
      { id: 'r14', generation: 45, name: '정승화', phone: '010-8859-4633', company: '', imgUrl: '' }
    ];

    const defaultPastSpecial = [
      { id: 's4', generation: 7, name: '김정수', phone: '010-4655-4245', company: '자영업', imgUrl: '' },
      { id: 's9', generation: 9, name: '박창식', phone: '010-3567-3845', company: '청와축산 대표/㈜제이피앤케이 대표', imgUrl: '' },
      { id: 's7', generation: 10, name: '김병섭', phone: '010-3568-8899', company: '나르미특장차 영남지역 영업지원실 실장', imgUrl: '' },
      { id: 's8', generation: 11, name: '이판우', phone: '010-9485-6567', company: '자영업', imgUrl: '' },
      { id: 's15', generation: 13, name: '정철식', phone: '010-6590-1485', company: '자영업', imgUrl: '' },
      { id: 's14', generation: 14, name: '허상회', phone: '010-8673-2388', company: '시민금방 대표', imgUrl: '' },
      { id: 's13', generation: 20, name: '한경수', phone: '010-4582-5440', company: '동창원직업소개소 대표', imgUrl: '' },
      { id: 's32', generation: 21, name: '정상철', phone: '010-4696-8887', company: '㈜동명 대표, ㈜계명목재 대표', imgUrl: '' },
      { id: 's40', generation: 22, name: '이영주', phone: '010-3843-4824', company: '회장', imgUrl: '' }
    ];

    function getSafeLocalData(key, defaultData) {
      try {
        const stored = localStorage.getItem(key);
        return stored ? JSON.parse(stored) : defaultData;
      } catch (e) {
        console.error("Local storage error on", key, e);
        return defaultData; // 만약 기존 데이터가 깨졌으면 기본값으로 복구하여 앱 멈춤 방지
      }
    }

    let state = {
      isLoggedIn: localStorage.getItem('scw_isLoggedIn') === 'true',
      userRole: localStorage.getItem('scw_userRole') || '',
      activeTab: 'regular',
      pastTab: 'lom',
      searchQuery: '',
      regularMembers: getSafeLocalData('scw_regular', defaultRegular),
      specialMembers: getSafeLocalData('scw_special', defaultSpecial),
      pastLom: getSafeLocalData('scw_pastLom', defaultPastLom),
      pastSpecial: getSafeLocalData('scw_pastSpecial', defaultPastSpecial),
      selectedItem: null,
      modalType: null,
      isEditing: false,
      editData: {}
    };

    function saveData() {
      localStorage.setItem('scw_regular', JSON.stringify(state.regularMembers));
      localStorage.setItem('scw_special', JSON.stringify(state.specialMembers));
      localStorage.setItem('scw_pastLom', JSON.stringify(state.pastLom));
      localStorage.setItem('scw_pastSpecial', JSON.stringify(state.pastSpecial));
      localStorage.setItem('scw_isLoggedIn', state.isLoggedIn);
      localStorage.setItem('scw_userRole', state.userRole);
    }

    function showToast(message) {
      const toast = document.getElementById('toast');
      toast.innerText = message;
      toast.classList.add('show');
      setTimeout(() => { toast.classList.remove('show'); }, 3000);
    }

    function exportVCard(name, phone, company, role) {
      const vcard = `BEGIN:VCARD\nVERSION:3.0\nN:;${name};;;\nFN:${name}\nORG:새창원청년회의소;${company || ''}\nTITLE:${role || ''}\nTEL;TYPE=CELL:${phone}\nEND:VCARD`;
      const blob = new Blob([vcard], { type: 'text/vcard;charset=utf-8' });
      const url = URL.createObjectURL(blob);
      const link = document.createElement('a');
      link.href = url;
      link.setAttribute('download', `${name}_연락처.vcf`);
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
      showToast('연락처가 다운로드 되었습니다.');
    }

    function exportCSV(type) {
      const list = type === 'regular' ? state.regularMembers : state.specialMembers;
      let csv = "\uFEFF구분,이름,연락처,직책,직장명,입회연도\n";
      list.forEach(m => {
        csv += `${type === 'regular' ? '정회원' : '특우회원'},${m.name},${m.phone},${m.role || ''},${m.company || ''},${m.joinYear || ''}\n`;
      });
      const blob = new Blob([csv], { type: 'text/csv;charset=utf-8;' });
      const url = URL.createObjectURL(blob);
      const link = document.createElement('a');
      link.href = url;
      link.setAttribute('download', `새창원JC_${type === 'regular' ? '정회원' : '특우회원'}_명단.csv`);
      document.body.appendChild(link);
      link.click();
      document.body.removeChild(link);
      showToast('엑셀 파일이 다운로드 되었습니다.');
    }

    function syncMemberInfoGlobally(updatedMember) {
      const syncList = (list) => {
        list.forEach(m => {
          if ((m.id === updatedMember.id) || (m.name === updatedMember.name && m.name.length > 1)) {
            m.name = updatedMember.name;
            m.phone = updatedMember.phone;
            m.company = updatedMember.company;
            if (updatedMember.imgUrl !== undefined) m.imgUrl = updatedMember.imgUrl;
          }
        });
      };
      syncList(state.regularMembers);
      syncList(state.specialMembers);
      syncList(state.pastLom);
      syncList(state.pastSpecial);
    }

    function initiateTransfer(targetCategory) {
      const item = state.selectedItem;
      if (!item) return;

      if (targetCategory === 'regular' || targetCategory === 'special') {
        let mIdx = state.regularMembers.findIndex(x => x.id === item.id);
        let sIdx = state.specialMembers.findIndex(x => x.id === item.id);
        let m = null;

        if (mIdx !== -1) m = state.regularMembers.splice(mIdx, 1)[0];
        else if (sIdx !== -1) m = state.specialMembers.splice(sIdx, 1)[0];

        if (!m) m = { ...item }; // 만약 역대회장 명단에서 호출한 경우 객체 복사

        m.type = targetCategory;
        m.role = ''; 
        
        if (targetCategory === 'regular') state.regularMembers.push(m);
        else state.specialMembers.push(m);

        saveData();
        closeModal();
        showToast(targetCategory === 'regular' ? '✅ 정회원으로 이동되었습니다.' : '✅ 특우회원으로 이동되었습니다.');
      } else if (targetCategory === 'pastLom' || targetCategory === 'pastSpecial') {
        state.editData = { ...item };
        state.editData.type = targetCategory === 'pastLom' ? 'lom' : 'special';
        state.editData.generation = ''; 
        state.selectedItem = null;
        state.modalType = 'past';
        state.isEditing = true;
        render();
        showToast('👉 역대회장 등록을 위해 기수(대수)를 입력 후 저장해주세요.');
      }
    }

    function render() {
      const app = document.getElementById('app');
      app.innerHTML = '';

      if (!state.isLoggedIn) {
        app.innerHTML = `
          <div class="flex-1 flex flex-col justify-center items-center p-6 bg-gradient-to-br from-blue-100 via-white to-blue-50 min-h-screen">
            <div class="w-full max-w-sm bg-white p-8 rounded-3xl shadow-xl border border-gray-100 flex flex-col items-center relative overflow-hidden">
              <div class="absolute top-0 left-0 w-full h-2 bg-blue-700"></div>
              <div class="w-24 h-24 bg-blue-700 rounded-2xl shadow-lg flex items-center justify-center text-white text-3xl font-black mb-6 tracking-tighter">JC</div>
              <h1 class="text-2xl font-black text-gray-800 mb-2">새창원청년회의소</h1>
              <p class="text-sm text-gray-500 mb-8 font-bold">통합 모바일 수첩</p>
              <form id="loginForm" class="w-full space-y-4">
                <div><input type="text" id="loginId" placeholder="아이디" autocomplete="off" class="w-full px-5 py-3.5 border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-500 bg-gray-50 text-base font-bold transition-all" /></div>
                <div><input type="password" id="loginPw" placeholder="비밀번호" autocomplete="off" class="w-full px-5 py-3.5 border border-gray-200 rounded-xl focus:outline-none focus:ring-2 focus:ring-blue-500 bg-gray-50 text-base font-bold transition-all" /></div>
                <button type="submit" class="w-full bg-blue-700 text-white font-black py-4 rounded-xl hover:bg-blue-800 transition shadow-md text-lg mt-2">안전하게 입장하기</button>
              </form>
              <p class="text-xs text-gray-400 mt-6 text-center">접속 오류 시 아이디와 비밀번호에<br/>'reset'을 입력하시면 초기화됩니다.</p>
            </div>
          </div>
        `;
        document.getElementById('loginForm').onsubmit = (e) => {
          e.preventDefault();
          const id = document.getElementById('loginId').value.trim();
          const pw = document.getElementById('loginPw').value.trim();
          
          if (id === 'reset' && pw === 'reset') {
            localStorage.clear();
            location.reload();
            return;
          }

          if (id === 'admin' && pw === '1234') {
            state.isLoggedIn = true;
            state.userRole = 'admin';
            saveData();
            render();
            showToast('✅ 관리자 모드로 접속했습니다.');
          } else if (id === '8677' && pw === '8677') {
            state.isLoggedIn = true;
            state.userRole = 'user';
            saveData();
            render();
            showToast('✅ 회원님 환영합니다.');
          } else {
            showToast('❌ 아이디 또는 비밀번호가 맞지 않습니다.');
          }
        };
        return;
      }

      app.innerHTML = `
        <div class="bg-blue-800 text-white p-4 shadow-md sticky top-0 z-20 flex items-center justify-between">
          <h1 class="text-lg font-black tracking-tight">새창원JC 회원수첩</h1>
          <div class="flex items-center space-x-3">
            <span class="text-[10px] bg-white/20 px-2.5 py-1 rounded-full font-bold tracking-wide">${state.userRole === 'admin' ? '관리자' : '일반회원'}</span>
            <button onclick="logout()" class="text-xs bg-white text-blue-800 hover:bg-blue-50 font-black px-3 py-1.5 rounded-full shadow-sm transition">종료</button>
          </div>
        </div>

        <div class="flex border-b border-gray-200 bg-white sticky top-[60px] z-20 text-sm shadow-sm">
          <button onclick="switchTab('regular')" class="flex-1 py-3.5 text-center font-black transition-colors ${state.activeTab === 'regular' ? 'text-blue-800 border-b-2 border-blue-800 bg-blue-50/50' : 'text-gray-500 hover:bg-gray-50'}">정회원</button>
          <button onclick="switchTab('special')" class="flex-1 py-3.5 text-center font-black transition-colors ${state.activeTab === 'special' ? 'text-blue-800 border-b-2 border-blue-800 bg-blue-50/50' : 'text-gray-500 hover:bg-gray-50'}">특우회원</button>
          <button onclick="switchTab('past')" class="flex-1 py-3.5 text-center font-black transition-colors ${state.activeTab === 'past' ? 'text-blue-800 border-b-2 border-blue-800 bg-blue-50/50' : 'text-gray-500 hover:bg-gray-50'}">역대회장</button>
          <button onclick="switchTab('rules')" class="flex-1 py-3.5 text-center font-black transition-colors ${state.activeTab === 'rules' ? 'text-blue-800 border-b-2 border-blue-800 bg-blue-50/50' : 'text-gray-500 hover:bg-gray-50'}">정관/규정</button>
        </div>

        <div class="flex-1 overflow-y-auto bg-gray-100 pb-24 relative scroll-smooth" style="min-height: calc(100vh - 120px);">
          ${renderTabContent()}
        </div>

        ${state.selectedItem ? renderModal() : ''}
        ${state.isEditing ? renderEditModal() : ''}
      `;
    }

    function renderTabContent() {
      if (state.activeTab === 'regular' || state.activeTab === 'special') {
        const list = state.activeTab === 'regular' ? state.regularMembers : state.specialMembers;
        const q = state.searchQuery.toLowerCase();
        let filtered = list.filter(m => m.name.toLowerCase().includes(q) || (m.role && m.role.toLowerCase().includes(q)) || (m.phone && m.phone.includes(q)) || (m.company && m.company.toLowerCase().includes(q)));
        
        if (state.activeTab === 'regular') {
          filtered.sort((a, b) => {
            if (!a.joinYear && !b.joinYear) return 0;
            if (!a.joinYear) return 1;
            if (!b.joinYear) return -1;
            return a.joinYear.localeCompare(b.joinYear);
          });
        }

        return `
          <div class="p-4">
            <div class="flex space-x-2 mb-4">
              <input type="text" placeholder="이름, 직책, 연락처, 직장 검색" value="${state.searchQuery}" oninput="handleSearch(this.value)" class="flex-1 p-3 border border-gray-200 rounded-xl text-sm font-bold focus:outline-none focus:ring-2 focus:ring-blue-500 shadow-sm bg-white" />
              <button onclick="exportCSV('${state.activeTab}')" class="bg-gray-800 hover:bg-gray-900 text-white px-4 rounded-xl text-sm font-bold shadow-sm shrink-0 transition">엑셀다운</button>
            </div>
            <div class="space-y-3">
              ${filtered.map(m => `
                <div onclick="openMemberModal('${m.id}', '${state.activeTab}')" class="bg-white p-4 rounded-2xl shadow-sm border border-gray-200 flex items-center justify-between cursor-pointer hover:shadow-md transition">
                  <div class="flex items-center space-x-4">
                    <div class="w-14 h-14 bg-gray-100 rounded-full flex items-center justify-center text-gray-400 overflow-hidden shrink-0 border border-gray-200">
                      ${m.imgUrl ? `<img src="${m.imgUrl}" class="w-full h-full object-cover"/>` : `<svg class="w-7 h-7" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd"></path></svg>`}
                    </div>
                    <div>
                      <div class="flex items-center space-x-2">
                        <h3 class="font-black text-gray-900 text-base">${m.name}</h3>
                        ${m.role ? `<span class="text-[10px] bg-blue-50 text-blue-700 px-2 py-0.5 rounded font-black border border-blue-100">${m.role}</span>` : ''}
                      </div>
                      <p class="text-gray-600 text-sm mt-1 font-bold">${m.phone || '연락처 없음'}</p>
                      ${m.company ? `<p class="text-xs text-gray-500 mt-0.5 truncate max-w-[160px] font-medium">${m.company}</p>` : ''}
                    </div>
                  </div>
                  <div class="flex flex-col space-y-2" onclick="event.stopPropagation()">
                    <a href="tel:${m.phone}" class="w-10 h-10 bg-green-50 text-green-600 rounded-full flex items-center justify-center shadow-sm hover:bg-green-100 transition text-lg">📞</a>
                  </div>
                </div>
              `).join('')}
              ${filtered.length === 0 ? '<div class="text-center py-12 text-gray-400 font-bold">검색 결과가 없습니다.</div>' : ''}
            </div>
            ${state.userRole === 'admin' ? `<button onclick="openAddModal('${state.activeTab}')" class="fixed bottom-6 right-6 w-14 h-14 bg-blue-700 text-white rounded-full shadow-lg flex items-center justify-center text-3xl font-light hover:bg-blue-800 hover:scale-105 transition-all z-30">+</button>` : ''}
          </div>
        `;
      }

      if (state.activeTab === 'past') {
        const list = state.pastTab === 'lom' ? state.pastLom : state.pastSpecial;
        const q = state.searchQuery.toLowerCase();
        let filtered = list.filter(p => p.name.toLowerCase().includes(q) || String(p.generation).includes(q) || (p.company && p.company.toLowerCase().includes(q)) || (p.phone && p.phone.includes(q)));
        filtered.sort((a, b) => a.generation - b.generation);

        return `
          <div class="flex flex-col h-full">
            <div class="flex p-4 bg-white border-b border-gray-100 space-x-3 shrink-0">
              <button onclick="switchPastTab('lom')" class="flex-1 py-3 rounded-xl text-sm font-black transition-all ${state.pastTab === 'lom' ? 'bg-blue-800 text-white shadow-md' : 'bg-gray-100 text-gray-500 hover:bg-gray-200'}">역대 회장</button>
              <button onclick="switchPastTab('special')" class="flex-1 py-3 rounded-xl text-sm font-black transition-all ${state.pastTab === 'special' ? 'bg-blue-800 text-white shadow-md' : 'bg-gray-100 text-gray-500 hover:bg-gray-200'}">역대 특우회장</button>
            </div>
            <div class="p-4 space-y-3 pb-20">
              <div class="mb-4">
                <input type="text" placeholder="기수, 이름, 직장명 검색..." value="${state.searchQuery}" oninput="handleSearch(this.value)" class="w-full p-3 border border-gray-200 rounded-xl text-sm font-bold focus:outline-none focus:ring-2 focus:ring-blue-500 shadow-sm bg-white" />
              </div>
              ${filtered.map(p => `
                <div onclick="openPastModal('${p.id}', '${state.pastTab}')" class="bg-white p-4 rounded-2xl shadow-sm border border-gray-200 flex items-center justify-between cursor-pointer hover:shadow-md transition">
                  <div class="flex items-center space-x-4">
                    <div class="w-14 h-14 bg-gray-100 rounded-full flex items-center justify-center text-gray-400 overflow-hidden shrink-0 border border-gray-200">
                      ${p.imgUrl ? `<img src="${p.imgUrl}" class="w-full h-full object-cover"/>` : `<svg class="w-7 h-7" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd"></path></svg>`}
                    </div>
                    <div>
                      <div class="flex items-center space-x-2">
                        <span class="text-xs font-black text-white bg-blue-600 px-2 py-0.5 rounded">${p.generation}대</span>
                        <h3 class="font-black text-gray-900 text-base">${p.name}</h3>
                      </div>
                      <p class="text-gray-600 text-sm mt-1 font-bold">${p.phone || '연락처 없음'}</p>
                      ${p.company ? `<p class="text-xs text-gray-500 mt-0.5 font-medium truncate max-w-[150px]">${p.company}</p>` : ''}
                    </div>
                  </div>
                  <div class="flex flex-col space-y-2" onclick="event.stopPropagation()">
                    <a href="tel:${p.phone || '#'}" class="w-10 h-10 ${p.phone ? 'bg-green-50 text-green-600 hover:bg-green-100' : 'bg-gray-50 text-gray-300 pointer-events-none'} rounded-full flex items-center justify-center shadow-sm transition text-lg">📞</a>
                  </div>
                </div>
              `).join('')}
              ${filtered.length === 0 ? '<div class="text-center py-12 text-gray-400 font-bold">등록된 정보가 없습니다.</div>' : ''}
            </div>
            ${state.userRole === 'admin' ? `<button onclick="openAddPastModal('${state.pastTab}')" class="fixed bottom-6 right-6 w-14 h-14 bg-blue-700 text-white rounded-full shadow-lg flex items-center justify-center text-3xl font-light hover:bg-blue-800 hover:scale-105 transition-all z-30">+</button>` : ''}
          </div>
        `;
      }

      if (state.activeTab === 'rules') {
        return `
          <div class="p-5 bg-white min-h-full pb-32 text-gray-800 text-[13px] leading-relaxed rules-content selection:bg-blue-200">
            
            <div class="doc-title">정관 및 제규정</div>

            <h3>제1장 총 칙</h3>
            <p><strong>제1조(명칭)</strong> 본 회는 새창원청년회의소(Junior Chamber International-SaeChangWon)이라 한다.</p>
            <p><strong>제2조(소속)</strong> 본 회는 JCI 국가단위 사단법인 한국청년회의소의 지방단위회로 소속되어 있다.</p>
            <p><strong>제3조(사무국)</strong> 본회 사무국은 창원시내에 둔다.</p>
            <p><strong>제4조(목적)</strong> 본회는 JC신조를 받들어 민주시민으로서의 훈련을 통하여 회원 개인의 지도역량을 개발하고 상호의 이해와 우의를 증진시키며 우리의 지역사회를 개발하며 나아가 전 인류의 번영을 기하고 세계의 평화에 이바지함을 목적으로 한다.</p>
            <p><strong>제5조(사업)</strong> 본 회의 목적을 달성하기 위하여 아래와 같은 사업을 실시한다.<br/>
            1. 본회 회원 개인의 지도역량을 개발하고 상호 이해와 우의를 증진시킬 수 있는 사업<br/>
            2. 우리가 속해있는 지역 사회 개발을 위한 각종의 사업 계획 수립과 집행에 관한 사업<br/>
            3. 우리가 속해있는 전체시민으로 하여금 시민으로서의 의무를 자각시키고 이를 완수토록 계몽하는 사업<br/>
            4. 한국청년회의소 및 경남. 울산 지구청년회의소의 중점사업 추진과 관련된 사업<br/>
            5. 청년단체 및 사회단체와의 유대를 강화할 수 있는 사업<br/>
            6. 국제간의 이해와 우의증진을 도모할 수 있는 사업<br/>
            7. 기타 본 회의 목적달성에 필요한 사업</p>
            <p><strong>제6조(운영의원칙)</strong> 본 회는 어느 개인이나 특정의 정당, 종교 또는 공공단체, 사회단체의 이익을 위하여 활동하지 않으며 이 단체로부터 지시나 감독을 받지 않는다.</p>
            <p><strong>제7조(사업년도)</strong> 본 회의 사업연도는 매년 1월 1일부터 동년 12월 31일까지로 한다.</p>

            <h3>제2장 회 원</h3>
            <p><strong>제8조(회원)</strong> 본 회의 회원은 정회원, 준회원, 부인회원, 특우회원, 명예회원으로 구분한다.</p>
            <p><strong>제9조(자격)</strong><br/>
            1. 정회원은 만20세 이상 만45세까지의 신망있고 성실한 청년으로서 한국JC 훈련원 교육을 이수한 자로 한다.<br/>
            2. 정회원으로서 연도 중에 만45세가 되더라도 그 연도말까지 정회원으로서의 자격을 갖는다.<br/>
            3. 회원으로 가입승인 받은 자로 한국JC 훈련원교육 미수료자는 준회원으로 한다.(단, 준회원은 입회 후 가입승인일로부터 1년 이내 1단계 연수를 필히 이수하여야 한다.)<br/>
            4. 직전회장은 제한연령을 초과하더라도 그 직책을 수행하는 기간 동안 정회원의 자격을 갖는다.<br/>
            5. 부인회원은 정회원 및 준회원의 부인으로 한다.<br/>
            6. 특우회원은 정회원으로 재직 제한연령을 초과하여 특우회에 가입한자로 한다.<br/>
            7. 명예회원은 본 회의 발전에 공헌이 있는 자로 이사회 의결로써 결정한다.</p>
            <p><strong>제10조(회원의 가입)</strong> 본회 회원이 되고자 하는 자는 회원자격규정 제 3조에 의거 승인을 받은 자로 한다.</p>
            <p><strong>제11조(정회원의 권리)</strong><br/>
            1. 본 회의 선거직 임원에 대한 선거권과 피선거권을 갖는다.<br/>
            2. 본 회가 소집하는 모든 회의의 의결권을 갖는다.<br/>
            3. 본 회의 선거직 임원에 대한 불신임 결의안 제출권을 갖는다.<br/>
            4. 본회 목적에 필요한 사업에 참여할 평등한 권리를 갖는다.</p>
            <p><strong>제12조(기타회원의 권리)</strong> 준회원, 특우회원, 명예회원은 발언권은 있으나 선거권과 피선거권 및 의결권은 없다.</p>
            <p><strong>제13조(정회원 및 준회원의 의무)</strong><br/>
            1. JCI 이념과 신조를 지켜야 할 의무<br/>
            2. 정관 및 제규정을 지켜야 할 의무<br/>
            3. 본회 목적달성에 필요한 사업에 대하여 적극 협조하여야 할 의무<br/>
            4. 모든 집회에 출석할 의무<br/>
            5. 제의무금을 납부할 의무<br/>
            6. 중앙훈련원 및 연수교육을 수료할 의무</p>
            <p><strong>제14조(포상)</strong><br/>
            1. 본 회의 발전과 품위 격상에 현저한 공로가 있는 회원에게는 회장은 이를 포상한다.<br/>
            2. 포상에 관한 사항은 별도 규정으로 정한다.</p>
            <p><strong>제15조(퇴회 및 복직)</strong><br/>
            1. 자퇴하고자 하는 정회원은 소정의 절차에 따라 퇴회신고를 하며 연도 중에 퇴회하더라도 그 연도에 제의무금을 납부하여야 한다. 단, 퇴회 신고후 1달 이내 제의무금을 납부하지 않았을 시 자동 제명 처리한다.<br/>
            2. 제명된 자는 본 회 회원으로 가입할 수 없다.(단, 소청심사위원회 운영규정에 의거 승인된 자는 복적할 수 있다.)<br/>
            3. 자퇴한자는 복적 신청 할 수 있다.(단, 자퇴한 년도 회비 완납 및 자퇴 년도 이후부터 복적 신청하는 년도까지의 전체 회비를 전액 완납하여야 한다.)<br/>
            4. 기타 납부한 회비에 대한 반환을 청구할 수 없다.</p>
            <p><strong>제16조(징계)</strong><br/>
            1. 본 회의 회원 중 아래 각호에 해당하는 경우 사무국장은 회원의 징계사유를 이사회에 보고 상정하여 의결로 이를 결정한다.<br/>
            1) 본 회의 명예를 손상시킨 경우<br/>
            2) 본 회의 질서를 심히 문란 시킨 경우<br/>
            3) 본 회의 월례회 및 총회에 사유 없이 계속 3회 이상 불참 및 연 6회 이상 불참한 경우<br/>
            4) 회원자격규정 제2조의 정한 자격을 미 이행한 경우<br/>
            5) 소정의 회비가 3개월 이상 체납하였을 경우<br/>
            6) 의무금을 발생일 이후 3개월 이내에 납부하지 않은 경우<br/>
            7) 명예회원으로서 본 회 발전이나 참여가 없을 경우<br/>
            8) 기타 본 회의 정관과 제 규정을 성실하게 준수하지 않음이 인정된 경우<br/>
            2. 회기 중 3회 이상 징계 받은 회원은 제명처리 된다.<br/>
            3. 당해 연도 회비 및 제반 의무금을 9월 30일까지 납부하지 않은 회원은 10월 1일자로 제명처리 된다.<br/>
            4. 징계를 받은 회원은 총회에서 이사회 결정에 대하여 재심을 청구할 수 있으며, 총회는 과반수이상의 의결로써 이를 결정하다.<br/>
            5. 징계 받은 회원은 징계결정일로부터 25일 이내 소청 심사위원회에 재심 청구를 할 수 있다.(단, 기한 만료일이 공휴일일 경우에는 익일을 만료일로 한다.)<br/>
            6. 징계종류는 경고, 해임, 자격정지(6개월 이내), 제명으로 한다.<br/>
            7. 입회 후 1년 이내 1단계 연수를 필하지 아니한 자는 자동 제명 처리한다.(단, 준회원 신상에 문제가 발생 시 당월 이사회를 거쳐 1회에 한해서 6개월의 유예기간을 둔다.)<br/>
            8. 명예회원은 당해 년도 회비를 12월 31일까지 납부하지 않을 시 자동 제명 처리된다.</p>
            <p><strong>제17조(소청심사)</strong> 회원의 권리관계 청원 및 총회, 월례회, 이사회 결정사항에 대한 이의제기 또는 정관유권해석 요청이 있을 시 소청심사위원회 운영 규정에 의거 심의 결정한다.</p>
            <p><strong>제18조(휴적)</strong> 부득이한 사유로 장기간 출석할 수 없는 정회원은 이사회의 승인을 받아 일정한 기간동안 휴적할 수 있다. 단, 휴적 중 이라도 회비는 면제되지 않는다.</p>
            <p><strong>제19조(회원자격의 상실)</strong> 본회의 회원은 다음 각 호에 해당될 때 그 자격을 상실한다. 1. 퇴회 2. 제명 3. 금치산 및 한정치산의 선고</p>

            <h3>제3장 총 회</h3>
            <p><strong>제20조(구성)</strong> 본 회 총회는 정회원, 준회원으로 한다.</p>
            <p><strong>제21조(종류)</strong> 본 회 총회는 정기총회와 임시총회로 한다.</p>
            <p><strong>제22조(총회의 소집)</strong><br/>
            1. 정기총회는 매년 1월에 회장이 소집한다.<br/>
            2. 임시총회는 다음 각 호의 1에 해당할 때 회장이 소집한다.<br/>
            1) 회장이 필요하다고 인정할 때 2) 이사회가 소집의 필요를 의결할 때 3) 재적회원 3분의 1 이상이 총회의 목적되는 사항을 서면으로 명시하여 소집 요구가 있을 때 4) 감사의 소집요구가 있을 때<br/>
            3. 2항 3호, 4호에 의한 총회는 소집의 요구를 접수한 날로부터 15일 이내에 소집하여야 한다.<br/>
            4. 차기연도 선거직 임원 선출을 위한 총회는 이사회에서 결정한다.<br/>
            5. 총회를 소집할 때는 회의의 목적되는 사항과 일시, 장소를 서면으로 기재하여 총회 개최 3일전까지 총회 구성원에게 통지하여야 한다.<br/>
            6. 월례회시 총회의 목적되는 사항을 명시하여 회장이나 감사 또는 재적회원 3분의 1 이상이 총회 개최 요구를 할 때에는 월례회를 임시총회로 바꿀 수 있다.</p>
            <p><strong>제23조(총회의 성립과 의결)</strong><br/>
            1. 총회의 의장은 회장이 된다.<br/>
            2. 총회의 재적 정회원수의 과반수 출석으로 성립되며 특별한 규정이 없는 한 출석 정회원수 과반수 찬성으로 의결한다.<br/>
            3. 가부동수일 경우에는 임원의 선출을 제외하고는 의장이 결정권을 가진다.<br/>
            4. 제24조 제1항 1호, 2호, 6호 및 선거직 임원의 해임 및 월회비 인상에 관하여는 출석 정회원수의 3분의 2 이상 찬성으로 의결한다.</p>
            <p><strong>제24조(총회의 의결사항)</strong><br/>
            1. 다음 각 호의 사항은 총회의 의결을 받아야 한다.<br/>
            1) 정관의 개정 2) 정관 시행을 위한 규정, 세칙 제정이나 개정 3) 선거직 임원의 선임 및 해임 4) 예산 및 결산의 승인 5) 사업계획 및 사업보고의 승인 6) 본회의 법적 지위 변경 또는 해산 및 잔여재산의 처분방법 결정 7) 규정에서 정한 총회의 의결사항 승인 8) 월 회비 인상에 따른 의결 사항 9) 기타 본 회의 운영에 특히 중요한 사항<br/>
            2. 총회에서는 회의소집 통지서에 기재된 안건에 대하여서만 심의할 수 있다. 다만, 총회에서 출석 정회원수의 과반수가 긴급하다고 인정하여 의안으로 채택한 것은 이를 심의할 수 있다.<br/>
            3. 총회의 의사에 관하여는 총회 종료 후 지체 없이 의사록을 작성하여야 하며 의사록에는 회장이 지명하는 2인의 정회원이 날인하여야 한다.</p>

            <h3>제4장 임 원</h3>
            <p><strong>제25조(임원의 종류와 수)</strong><br/>
            1. 본 회의 선거직 임원은 아래와 같다.<br/>
            1) 회장 1명 2) 상임부회장 1명 3) 내무부회장 1명 4) 외무부회장 1명 5) 감사 2명<br/>
            2. 당연직 임원은 아래와 같다.<br/>전임회장은 직전회장이 된다. 직전회장은 본 회의소 선거관리위원장으로서 회장의 자문에 응하고 선거관리에 관한 제반 업무를 집행한다.<br/>
            3. 본 회의소의 임명직 임원은 아래와 같다.<br/>1) 사무국장 2) 이사 3) 분과위원장<br/>
            4. 본 회의 원활한 운영을 위하여 회장이 원하는 별도의 자문기구를 총회의 승인을 얻어 둘 수 있다.</p>
            <p><strong>제26조(임원의 자격과 임원의 임명)</strong><br/>
            1. 회장은 본 회의 만 3년 이상 재적하고 선거직 임원을 역임한 정회원이여야 한다.<br/>
            2. 부회장 및 감사는 3년 이상 재적한 정회원 중에서 총회를 거쳐 선임한다.<br/>
            3. 기타 세부사항은 본 회 선거직 임원의 선거관리 규정으로 정한다.<br/>
            4. 이사는 정회원으로 회장이 임명하여 총회에 보고한다.<br/>
            5. 본 회의 선거직 임원은 3단계 연수교육을 필한 정회원이여야 한다. (세부규정은 지구, 중앙에 준함)</p>
            <p><strong>제27조(선거직 임원의 선출 방법)</strong> 선거직 임원의 선출에 관한 사항은 임원선임에 관한 규정에 정하기로 한다.</p>
            <p><strong>제28조(선거직 임원의 임기)</strong><br/>
            1. 선거직 임원의 임기는 1년으로 한다.<br/>
            2. 1회에 한해서만 동일 직에 중임할 수 있다.<br/>
            3. 임기 중에 보선된 임원의 임기는 전임자의 잔여기간으로 한다.</p>
            <p><strong>제29조(입후보자 등록금)</strong> 선거직 임원 입후보자는 임원선임에 관한 규정 제14조 7항에 정한 금액을 회관건립기금으로 공탁하여야 한다.</p>
            <p><strong>제30조(임원의 결원과 해임)</strong><br/>
            1. 연도 중 선거직 임원이 결원되었을 때는 총회에서 보선한다.<br/>
            2. 임명직 임원이 동일 기관의 공식 집회에 특별한 사유 없이 3회 연6회 이상 출석하지 않을 때는 회장은 총회 또는 이사회의 승인에 관계하지 아니하고 해임하여야 한다.<br/>
            3. 임명직 임원이 임원 또는 회원의 품위를 가지지 못하거나 당해 업무를 수행할 능력이 없다고 판단될 때는 이사회의 결의에 따라 회장이 해임할 수 있다.<br/>
            4. 연도 중 임명직 임원이 결원되었을 때는 회장이 추천하여 이사회의 승인을 받아야 한다.<br/>
            5. 보선 또는 보임된 임원의 임기는 당해 사업년도의 잔여 임기로 한다.<br/>
            6. 제1항, 제4항에 있어 잔여 임기가 만 3개월 미만일 때는 보선 또는 보임하지 않을 수 있다.</p>

            <h3>제5장 임원의 임무</h3>
            <p><strong>제31조(회장의 업무)</strong> 회장은 본 회를 대표하여 대내적으로 모든 회무를 총괄하여 이사회 및 월례회의 의장이 된다.</p>
            <p><strong>제32조(회장의 궐위)</strong> 회장의 사망, 지체장애, 사임, 불신임결의, 기타사유로 유고 또는 궐위된 때는 후임 회장이 선출될 때까지 직전회장, 상임부회장, 내무부회장의 순으로 그 직무를 대행한다.</p>
            <p><strong>제33조(상임부회장 업무)</strong><br/>
            1. 회장을 보좌하며 회장의 명을 받아 본 회의소의 제반업무 및 사무국 업무를 집행 관장한다.<br/>
            2. 1) 내무부회장 2) 외무부회장 3) 사무국장의 업무를 관장한다.</p>
            <p><strong>제34조(내무부회장의 업무)</strong> 내무부회장은 회장을 보좌하고 본회의 운영에 따른 대내적인 업무와 총무이사 및 총무이사가 관장하는 기록포상, 의전운영, 체육우호 분과위원회와 재정이사 및 재정이사가 관장하는 회원확충분과, 지도력개발 위원회를 관장한다.</p>
            <p><strong>제35조(외무부회장의 업무)</strong> 외무부회장은 회장을 보좌하고 본회의 운영에 따른 대외적인 업무와 연수이사 및 연수이사가 관장하는 특우회 부인회 담당분과, 홍보활동 분과위원회와 기획이사 및 기획이사가 관장하는 국제활동, 청소년활동, 지역사회개발분과위원회를 관장한다.</p>
            <p><strong>제36조(감사)</strong><br/>
            1. 감사는 본 회의 업무 및 재산 상황을 감사하고 총회, 이사회, 월례회에 출석하여 그 의견을 발표한다.<br/>
            2. 감사는 총회시 특정사항에 관하여 감사보고서를 제출하여야 한다.</p>
            <p><strong>제37조(임명직 임원의 업무)</strong><br/>
            1. 사무국장은 회장의 지시를 받아 본 회의 제반업무를 처리하고 총회, 이사회, 월례회에 참석하여 발언권과 의결권을 갖는다.<br/>
            2. 각 이사 및 분과위원장은 회장을 보좌하여 그의 지시에 따라 소속 분과위원회를 주관한다.</p>

            <h3>제6장 기 관</h3>
            <p><strong>제38조(이사회 구성)</strong><br/>
            1. 이사회는 다음 각 호의 임원으로 구성한다.<br/>
            1) 회장 2) 직전회장 3) 부회장 4) 각 이사 5) 각 분과위원장 6) 사무국장 7) 감사 (단, 감사는 의결권이 없다.)</p>
            <p><strong>제39조(이사회의 소집)</strong><br/>
            1. 정기이사회는 매월 월례회 및 총회 전에 개최하는 것을 원칙으로 하고 회장이 소집한다.<br/>
            2. 임시이사회는 다음 각 호의 1에 해당될 때 회장이 소집한다.<br/>
            1) 회장이 필요하다고 인정할 때 2) 재적이사 3분의 1 이상이 회의의 목적되는 사항을 서면으로 명기하여 소집을 요구할 때 3) 위 제2호의 경우에는 회장은 특별한 사유가 없는 한 소집의 요구를 접수한 날로부터 7일 이내에 이사회를 소집하여야 한다.<br/>
            3. 이사회를 소집할 때에는 회장은 구성원에게 적어도 회의 1일전까지 회의의 목적 사항을 서면 또는 구두로 통지하여야 한다.<br/>
            4. 이사회의 의장은 회장이 된다.</p>
            <p><strong>제40조(이사회의 의결)</strong><br/>
            1. 이사회는 재적이사의 과반수 출석으로 특별한 규정이 없는 한 출석이사의 과반수 찬성으로 의결한다.<br/>
            2. 정관 제 16조 및 회원자격규정 3조를 의결할 시는 재적이사 과반수의 출석과 출석회원 2/3 이상의 찬성이 있어야 한다.<br/>
            3. 분과위원장의 의결권은 당해 분과의 전체 의사를 반영하는 것을 원칙으로 한다.</p>
            <p><strong>제41조(이사회의 의결사항)</strong> 이사회는 본 회의소의 총회 다음가는 의결기관으로서 아래와 같은 사항의 업무를 처리한다.<br/>
            1) 제규정의 재정과 개정에 관한 심의 의결 2) 운영방침과 사업계획 수립 3) 분과위원회의 담당활동에 대한 조정 4) 회원의 가입 및 징계 5) 총회, 월례회 개최 일자와 장소의 결정 6) 총회에 제출할 의안 7) 총회로부터 위임받은 사항 8) 기타 본 회의소 운영에 관한 중요한 사항</p>
            <p><strong>제42조(세칙)</strong> 이사회의 효율적 운영을 위하여 이사회 규정을 따로 정한다.</p>
            <p><strong>제43조(분과위원회의 설치)</strong><br/>
            1. 본 회의 목적달성을 위하여 아래와 같이 분과위원회를 둘 수 있다.<br/>
            1) 기록포상 분과위원회 2) 의전운영 분과위원회 3) 체육우호 분과위원회 4) 회원확충 분과위원회 5) 지도력개발 분과위원회 6) 특우회, 부인회담당 분과위원회 7) 홍보활동 분과위원회 8) 국제활동 분과위원회 9) 청소년활동 분과위원회 10) 지역사회개발 분과위원회<br/>
            2. 이사회에서 필요하다고 인정할 때에는 위의 위원회 외에 특수한 목적을 갖는 상설 또는 임시위원회를 설치 할 수 있다.</p>
            <p><strong>제44조(상임이사 및 분과위원회)</strong><br/>
            1. 본회에 다음의 상임이사를 두며 의무는 다음과 같다.<br/>
            1) 사무국장 : 사무국장은 회장을 비롯한 모든 임원을 행정적 보좌하며 사무국의 모든 업무를 회장단 또는 이사회 승인 하에 책임 처리하며 그 업무는 다음과 같다.<br/>
            ① 중앙, 지구 및 타지방 JC와 유기적 업무연락 및 업무처리 책임을 진다.<br/>
            ② 본회 운영을 위한 제반사업 실시 시 위원회와 유기적 업무 협조를 적극 기하고 성공적 달성을 위해 최대한 공조적 노력을 기한다.<br/>
            ③ 본 회의소 모든 사업 및 행사시 회원과 유관 일반인들에 대한 연락 및 참석 독려업무를 한다.<br/>
            2) 총무이사<br/>
            ① 본회 회무 회계 집행에 관하여 사무국의 소관 업무를 책임진다.<br/>
            3) 기획/재정이사<br/>
            ① 본회 회무 회계 집행에 관하여 사무국의 소관 업무를 책임진다.<br/>
            ② 총회, 이사회, 월례회시 회무, 재무상황을 매월 보고하여야 한다.<br/>
            ③ 본회행사 및 사업실시에 따른 사무국의 의전 업무를 책임진다.<br/>
            4) 연수이사<br/>
            ① 회원의 가치관 확립, 품위, 참여, 예의, 우정, 개인능력 개발 등에 따른 연수 업무를 책임진다.<br/>
            5) 특우회.부인회 담당이사<br/>
            ① 정회원과 특우회, 부인회원 간의 유대강화 및 제반사업을 위한 연락 업무 및 재정 협의 사항<br/>
            ② 정회원과 특우회, 부인회원 간의 협조체제를 강화하여 원만한 교류관계를 정립하는데 책임을 진다.<br/>
            7) 중앙임원 및 요원 : 본회 운영전반에 걸쳐 자문에 응한다.<br/>
            8) 지구임원 및 요원 : 본회 운영전반에 걸쳐 자문에 응한다.<br/>
            2. 본회에 다음의 분과위원회를 두며 업무는 다음과 같다.<br/>
            1) 기록포상분과위원회<br/>
            ① 회원의 표창 및 징계에 관한 사항 ② 대외표창에 관한 사항 ③ 장학사업에 관한 선발대상자 선임 업무 ④ 각종 활동에 대한 기록 및 표창에 관한 업무 ⑤ 중요기록, 관계 자료의 수집 보관<br/>
            2) 의전운영 분과위원회<br/>
            ① 행사 및 사업실시에 따른 사무국의 의전 업무를 책임진다. ② JC조직과 단체에 대한 올바른 이해와 의전에 대한 올바른 개념인식을 기본방침으로 의전의 필요성에 대한 교육에 관한 업무 ③ 신입회원에 대한 올바른 의전교육을 책임진다.<br/>
            3) 체육우호 분과위원회<br/>
            ① 회원 및 회원가족의 체력증진을 위한 사업의 연구 및 실시 ② 지역사회의 체육진흥을 위한 사업의 연구 및 실시 ③ 우호, 형제, 자매JC와 유대강화 및 상호간 사업추진 계획수립 공동추진 ④ 국내외 각JC와 교류 및 친목 유대강화 ⑤ 기타 체육진흥 및 우호증진에 관한 사업<br/>
            4) 회원확충 분과위원회<br/>
            ① 회원확충에 관한 제반사항 ② 신입회원 연수에 관한 사항 특우회 부인회 상호간 친선도모 사업 회원조직 강화<br/>
            5) 지도력개발 분과위원회<br/>
            ① 시민정신 함양사업 ② 청년지도자 정신 및 지도역량 개발을 우한 연수 및 교육 ③ JC회원의 연수관계 사업 ④ 회의 진행법 보급<br/>
            6) 지역홍보 분과위원회<br/>
            ① 대내외의 홍보에 관한 사무국 소관사항을 책임을 진다. ② 창립기념지등 본회 각종 간행물 편집 및 발간 ③ 기타 본회 홍보에 관한 사항 ④ 향토문화 창달을 위한 사업의 조사 연구 계획 및 실시 ⑤ 기타 지역사회의 발전에 과한 제반사항<br/>
            7) 국제활동 분과위원회<br/>
            ① 국제경제 협력 및 발전에 관한 제반사항<br/>
            8) 청소년활동 분과위원회<br/>
            ① 청소년 및 교육의 발전을 위한 제반사항에 관한 연구, 계획 및 그 사업의 실시<br/>
            3. 본회에 사무차장을 약간명을 두며 업무는 다음과 같다.<br/>
            1) 사무국장을 보좌하며 사무국 업무를 처리한다.<br/>
            2) 연락업무, 회원참석, 독려 업무, 각종 행사시 준비사항 점검</p>
            
            <p><strong>제45조(분과위원회 운영)</strong><br/>
            1. 위원회는 위원장과 회장이 지명하는 회원으로 구성한다.<br/>
            2. 위원회는 매월 위원장이 소집한다.<br/>
            3. 위원회는 소속위원 전원 출석을 원칙으로 한다.<br/>
            4. 위원회는 회의록을 작성하여 사무국에 비치한다.</p>

            <p><strong>제46조(분과위원회 업무)</strong><br/>
            1. 위원회는 소관 업무에 관한 조사연구 및 사업을 실시한다.<br/>
            2. 이사회에 부의할 의안을 채택 및 심의하여 회장단 회의에 제출한다.<br/>
            3. 이사회, 월례회시 보고서를 제출한다.<br/>
            4. 총회, 월례회 또는 이사회에서 위임받는 사항을 심의 결정한다.</p>

            <p><strong>제47조(자문위원회)</strong><br/>
            1. 본 회의 자문위원은 역대회장으로 한다.<br/>
            2. 자문위원회는 회관건립 및 관리기금을 관리 운용한다.<br/>
            3. 기금의 관리 운영은 규정으로 정한다.<br/>
            4. 사업계획에 대한 조언과 재심의 요구 및 선거직 임원에 대한 불신임 결의안을 심의하여 총회에 제출한다.</p>

            <p><strong>제48조(월례회의 종류)</strong><br/>
            1. 월례회는 정기월례회와 임시월례회로 구분한다.<br/>
            2. 정기월례회는 매월 개최하며 필요한 경우 임시 월례회를 개최할 수 있다.</p>

            <p><strong>제49조(월례회의 운영)</strong><br/>
            1. 월례회는 회장이 소집한다.<br/>
            2. 월례회는 성원 정족수를 두지 않는다.<br/>
            3. 월례회의 의장은 회장이 된다.<br/>
            4. 월례회의 JC회원 화합과 내부결속을 위하여 우호 및 형제자매, 인근 롬 JC합동월례회, 신입회원 환영회, 강연회, 공청회, 토론회, 야유회, 체육행사, 취미오락행사, 산업시찰, 기타행사 등으로 운영한다.</p>

            <h3>제7장 재 정</h3>
            <p><strong>제50조(회계)</strong><br/>
            1. 본회의 회계연도는 매년 1월 1일부터 12월 31일까지로 한다.<br/>
            2. 본회의 자산은 이월자산과 당해 사업년도의 회비, 가입금, 찬조금 및 기타 수입금으로 구성한다.<br/>
            3. 본회의 회계는 일반회계와 특별회계로 구분하여 처리한다.</p>

            <h3>제8장 관 리</h3>
            <p><strong>제51조(정관의 비치)</strong> 회장은 정관 및 제규정과 회원명부, 총회 및 월례회 이사회의 의사록을 항시 사무국에 비치하여야 한다.</p>
            <p><strong>제52조(보고서의 제출)</strong><br/>
            1. 직전회장은 매년 1월에 개최되는 정기총회 개최일로부터 15일전까지 회장 재임 사업년도(이하 전년도라 한다.)에 대한 다음 각 호의 서류를 작성하여 전년도의 감사에게 제출하여야 한다.<br/>
            1) 사업보고서 2) 결산서<br/>
            2. 전항의 서류를 접수한 전년도 감사는 엄정한 심사를 하여 당해 정기총회 개최 10일 전까지 의견서를 작성하여 직전회장에게 제출하여야 한다.<br/>
            3. 직전회장은 전항의 의견서가 첨부된 제1항의 서류를 당해 정기총회에 제출하여 승인을 받아야 한다.</p>

            <h3>제9장 사무국</h3>
            <p><strong>제53조(사무국)</strong> 본 회의 사무를 처리하기 위하여 사무국을 둔다.<br/>
            1. 사무국장은 회장 및 부회장을 보좌하며 회무를 처리하고 사무국을 통괄한다.<br/>
            2. 본 회는 그 업무를 처리하기 위하여 사무국에 직원 약간 명을 둘 수 있다.<br/>
            3. 사무국 운영에 관한 필요한 사항은 이사회에서 정한다.</p>

            <h3>제10장 정관개정</h3>
            <p><strong>제54조(개정)</strong> 본회 정관은 총회에서 출석 정회원 2/3이상의 찬성으로 개정할 수 있다.</p>
            <p><strong>제55조(시행규정)</strong><br/>
            1. 본 정관의 시행에 관한 세칙은 별도의 규정이 없는 한 이사회에서 정하기로 한다.<br/>
            2. 본 정관 또는 다른 규정에 되어 있지 않은 사항은 JCI와 사단법인 한국청년회의소 정관 및 제규정과 경남.울산지구청년회의소 정관의 제 규정을 준용한다.</p>

            <h3>제11장 임원의 해임</h3>
            <p><strong>제56조</strong> 다음 각 항에 해당하는 임원은 불신임 결의의 대상이 된다.<br/>
            1. 이사회에 연속 3회 불참한 임원<br/>
            2. 임무를 나태한 임원<br/>
            3. 본회 명예를 실추시킨 임원<br/>
            4. 본회 재정에 손실을 초래한 임원</p>

            <p><strong>제57조</strong> 선거직 임원의 불신임 결의는 다음과 같이 한다.<br/>
            1. 불신임 결의안은 회원 1/3이상의 서명으로 제출할 수 있다.<br/>
            2. 의장은 회장이 된다. 단, 회장이 불신임 대상일 때는 임시 의장을 선출하여 회의를 진행한다.<br/>
            3. 의결방법 : 무기명 비밀투표로 총회 출석 정회원수의 2/30이상의 찬성으로 의결한다.</p>

            <p><strong>제58조(임명직 임원의 해임)</strong><br/>
            1. 임명직 임원 해임 건의는 회장단 또는 회원 1/3이상의 서명으로 제출할 수 있다.<br/>
            2. 임명직 임원의 해임은 이사회 재적 2/3이상의 찬성으로 한다.<br/>
            3. 이사회 결정에 대한 이의 신청은 정관 제16조 10항, 11항에 준한다.</p>

            <p><strong>부칙</strong><br/>
            본 규정은 1981년 8월 2일부터 시행한다.<br/>
            '1998년 4월 18일 재정 (창립총회)<br/>
            '1982년 11월 3일 개정 (제4차 총회)<br/>
            '1984년 11월 6일 개정 (제8차 총회)<br/>
            '1985년 11월 5일 개정(제10차 총회)<br/>
            '1986년 8월 23일 개정 (제13차 총회)<br/>
            '1987년 7월 20일 개정 (제15차 총회)<br/>
            '1990년 1월 20일 개정 (제23차 총회)<br/>
            '1991년 2월 5일 개정 (제25차 총회)<br/>
            '1993년 2월 13일 개정 (제31차 총회)<br/>
            '1993년 11월 24일 개정 (제33차 총회)<br/>
            '1995년 1월 9일 개정 (제37차 총회)<br/>
            '1997년 8월 27일 개정 (제44차 총회)<br/>
            '1999년 2월 23일 개정 (제48차 총회)<br/>
            '2000년 3월 29일 개정 (제51차 총회)<br/>
            '2001년 9월 28일 개정 (제55차 총회)<br/>
            '2002년 9월 26일 개정 (제57차 총회)<br/>
            '2002년 10월 29일 개정(제58차 총회)<br/>
            '2003년 9월 24일 개정 (제60차 총회)<br/>
            '2003년 11월 6일 개정 (제61차 총회)<br/>
            '2004년 10월 13일 개정 (제63차 총회)<br/>
            '2005년 10월 7일 개정 (제65차 총회)<br/>
            '2006년 2월 2일 개정 (제66차 총회)<br/>
            '2007년 1월 26일 개정 (제69차 총회)<br/>
            '2007년 11월 7일 개정 (제70차 총회)<br/>
            '2008년 1월 24일 개정 (제71차 총회)<br/>
            '2009년 1월 21일 개정 (제73차 총회)<br/>
            '2010년 1월 28일 개정 (제75차 총회)<br/>
            '2011년 1월 25일 개정 (제77차 총회)<br/>
            '2013년 1월 29일 개정 (제81차 총회)<br/>
            '2015년 1월 29일 개정 (제85차 총회)<br/>
            '2016년 1월 26일 개정 (제87차 총회)<br/>
            '2017년 1월 19일 개정 (제90차 총회)<br/>
            '2017년 9월 25일 개정 (제91차 총회)<br/>
            '2018년 1월 23일 개정 (제92차 총회)<br/>
            '2019년 1월 28일 개정 (제94차 총회)<br/>
            '2020년 1월 29일 개정 (제96차 총회)<br/>
            '2022년 1월 27일 개정 (제101차 총회)<br/>
            '2024년 10월 24일 개정 (제106차 총회)<br/>
            '2025년 1월 23일 개정 (제107차 총회)</p>

            <div class="doc-title">회원자격규정</div>
            <p><strong>제1조(목적)</strong> 본 규정은 본회 회원의 자격취득 및 회원자격 유지 등에 관한 사항을 규정함을 목적으로 한다.</p>
            <p><strong>제2조(정회원의 자격)</strong> 제 3조의 가입절차에 의거 가입 승인을 받아 총회 또는 이사회에서 가입선서를 함으로써 준회원의 자격을 가지며 한국JC 신입회원 연수과정을 이수한 자는 정회원의 자격을 가진다.</p>
            <p><strong>제3조(가입절차)</strong> 본회 가입을 희망하는 자는 본회 정회원 2인의 추천과 1인 이사의 보증을 받아 제4조의 서류를 사무국에 제출하여 회원확충분과위원장의 예비심사를 거쳐 이사회 승인을 얻어 가입 선서를 함으로써 준회원의 자격을 가진다. (인준방법은 찬반 토론 없이 무기명 비밀투표로 한다.)<br/>
            1. 추천인은 본회 재적기간 1년 이상의 정회원으로서 제반 의무사항을 충실히 이행한 회원이어야 한다.<br/>
            2. 보증인은 신입회원 입회년도 당해년의 제반 의무금 및 의무사항에 대한 보증을 책임져야 한다.</p>
            <p><strong>제4조(가입서류)</strong> 본회 입회를 희망하는 자는 다음 각항의 서류를 제출하여야 한다.<br/>
            1) 가입신청서 1부 (별표 제1호) 2) 주민등록등본 3) 사진(증명사진 10매, 명함 10매)</p>
            <p><strong>제5조(회원의 납입의무금과 납입시기)</strong> 제3조의 규정에 의거 준회원으로 승인 받은 자의 가입금과 월 회비 납기일은 다음과 같다.<br/>
            1. 신입회원 가입금은 당해연도 정기총회에서 결정한다.<br/>
            2. 가입금 및 제반의무금은 이사회 승인일 이전까지 납부하여야 한다.<br/>
            3. 월 회비는 당해 월의 월례회시 납입토록 한다.<br/>
            4. 신입회원의 월 회비는 가입 승인된 당해 월부터 납입해야 한다.<br/>
            5. 명예회원은 가입 승인된 당해 연도 회비 36만원을 납부하여야 한다.</p>
            <p><strong>제6조(재적기간의 가산)</strong> 정회원의 본 회 재적기간은 다음 각 항에 따라 가산한다.<br/>
            1. 창립회원의 경우에는 본 회 창립일로부터<br/>
            2. 신입회원의 경우에는 가입 선서일로부터<br/>
            3. 전입한 회원의 경우에는 최초의 지방회의소 가입 승인일로부터<br/>
            4. 복적한 회원일 경우에는 복적 후 가입 선서일로부터(소청에 의한 복적은 그러하지 않는다.)<br/>
            5. 휴직한 회원일 경우에는 휴직기간을 제외하고 가산한다.</p>
            <p><strong>제7조(회원의 특정자격)</strong><br/>
            1. 본 회의 모든 정회원은 다음 각호와 같이 소정의 연수 교육을 이수하여야 한다.<br/>
            1) 신입회원 : 훈련원 교육<br/>
            2) 일반회원 : 연수교육<br/>
            3) 임원 : 임원연수교육<br/>
            2. 본 회의 선거직 임원은 제1항에 정하는 각호의 연수교육을 모두 이수한 자라야 한다.<br/>
            본 규정은 1994년 1월 1일부터 시행한다.</p>
            <p><strong>제8조(회비등의 분담금 납입 의무)</strong><br/>
            1. 회원 자격규정이 정하는 바에 따라 가입시에는 가입금을 납입하고 매년 정해진 회비를 소정의 기일 내에 납입하여야 한다.<br/>
            2. 가입금 및 회비 액수에 관하여 필요한 사항은 회원자격규정이 정하는 바에 따른다.<br/>
            3. 납입의무가 확정된 가입금, 회비, 기타 의무 분담금은 어떠한 이유로도 면제되지 않는다.<br/>
            4. 기 납입된 가입금 및 의무 분담금은 반환되지 않는다.<br/>
            5. 특별협찬금을 제외하고 총회에서 결정된 모든 기타 협찬금 및 분담금은 의무분담금으로 명칭 변경한다.</p>

            <div class="doc-title">회계규정</div>
            <h3>제1장 총 칙</h3>
            <p><strong>제1조(목적)</strong> 본 규정은 새창원청년회의소(이하 본회라 칭한다.) 정관 제41조의 규정에 의거 본회의 재무와 회계에 관한 기준을 확립하여 그 운영의 합리화를 도모하고 업무 집행의 원활을 기하는데 목적이 있다.</p>
            <p><strong>제2조(적용범위)</strong> 본회의 재무와 회계에 관하여는 비영리 법인에 적용 또는 준용되는 법령에 의하는 사항 외에는 본 규정이 정하는 바에 따른다.</p>
            <p><strong>제3조(세입세출의 정의와 회계연도)</strong><br/>
            1. 본 회의 회계연도는 1년을 1기로 하며 매년 1월 1일부터 12월 31일까지로 한다.<br/>
            2. 일반회계년도의 일체의 지출은 세출로 하고 이에 필요한 일체의 수입을 세입으로 한다.<br/>
            3. 회계처리의 원칙과 절차는 매 사업년도에 계속성 있게 적용하고 이를 임의로 변경할 수 없다.<br/>
            4. 본 회의 회계는 일반회계와 특별회계로 명확하게 구분 처리한다.<br/>
            5. 상기 각호의 규정한 이외의 관하여는 기타 일반적으로 공정 타당하다고 인정하는 비영리 법인의 회계원칙에 따른다.</p>
            <p><strong>제4조(기록 및 증명의 보존)</strong><br/>
            본 규정에 의한 모든 회계처리는 그 회계처리를 구체적으로 증명할 수 있도록 장부를 기장하되 그 기장을 증명하는 관계문서를 구비하여야 한다.</p>
            
            <h3>제2장 장표와 개정</h3>
            <p><strong>제5조(장표)</strong><br/>
            1. 회계장부는 다음 각호와 같이 구분하여 회계연도마다 갱신한다.<br/>
            1) 금전출납부 2) 총계정원장 3) 기타 보조부<br/>
            2. 전표의 종류는 다음 각호와 같이 구분한다.<br/>
            1) 입금전표 2) 출금전표 3) 대체전표</p>
            <p><strong>제6조(수입과 지출)</strong> 수입과 지출에 관한 모든 거래는 전표에 의하여 기장 처리한다.</p>

            <h3>제3장 금전회계</h3>
            <p><strong>제7조(금전)</strong> 본 규정에서 금전이라 함은 현금과 예금을 말하며, 현금 외 통화의 보유중인 어음, 수표, 우편환 등을 포함한다.</p>
            <p><strong>제8조(예입)</strong> 입금된 금전은 특수한 경우를 제외하고는 당일 중에 잔액을 금융기관에 예입하여야 한다.</p>
            <p><strong>제9조(금융기관)</strong><br/>
            1. 금융기관의 예금거래를 개폐할 시에는 이사회 의결을 얻어야 한다.<br/>
            2. 특별회계의 기금은 본회의 명의로 하여 본회가 인정하는 인감을 사용하고 일반회계 은행 예금의 명의는 본 회의 인감을 사용한다.</p>
            <p><strong>제10조(예금의 인출)</strong> 예금의 인출은 재정이사, 상임부회장, 회장의 승인을 득하여 인출한다.</p>

            <h3>제4장 수지예산</h3>
            <p><strong>제11조(회계년도 귀속부분)</strong> 모든 수익과 비용은 그 발생한 날이 속하는 회계기간에 적정하게 계산한다. 다만, 그 원인이 되는 사실의 발생한 날을 정할 수 있는 그 사실을 확정한 날을 기준으로 한다.</p>

            <h3>제5장 예 산</h3>
            <p><strong>제12조(예산편성 절차)</strong> 예산은 회장 또는 그 위임을 받은 자가 편성하여 총회의 승인을 얻어야 한다.</p>
            <p><strong>제13조(가예산)</strong><br/>
            1. 본 회의 예산에 관하여 총회 승인을 얻지 못한 경우에는 총회 승인 시까지 회장은 인건비와 경상운영비에 한하여 전년도 예산에 준하여 가예산을 편성하고 예산이 승인될 때까지 이를 집행할 수 있다.<br/>
            2. 전항의 경우에는 전조의 규정에 불구하고 이사회의 승인을 얻음으로써 효력이 발생한다.</p>
            <p><strong>제14조(예산의 목적 외 사용금지)</strong> 본 회의 세출 예산은 목적 외에 이를 사용하지 못한다. 다만, 동일 예산내에서의 유용은 할 수 있되 제15조의 정하는 바에 따른다.</p>
            <p><strong>제15조(예산의 유용)</strong> 회장은 사업계획의 변경이나 집행 불가피한 사유로 각 계정 과목을 집행에 있어 예산을 유용하고자 하는 금액과 사유 및 유용으로 인한 효과 등을 논의 이사회의 의결을 거쳐 실행한다.</p>

            <h3>제6장 결 산</h3>
            <p><strong>제16조(결산)</strong> 결산은 익년도 1월 정기총회의 의결을 얻어야 하며 매 회계연도 말 결산서류에는 다음 각 조의 서류를 작성 첨부하여야 한다.<br/>
            1. 사업보고서 2. 재무보고서</p>

            <h3>제7장 보 칙</h3>
            <p><strong>제17조(결손 처리)</strong> 본회는 여하한 경우에도 채무에 대한 보증은 하지 못한다.</p>
            <p><strong>제18조(회계관리 직원의 책임)</strong> 본 회의 수입 지출 및 물품과 재산의 수급보관 또는 관리를 담당한 직원은 선량한 관리자로서의 임무와 의무를 다하지 못하여 손해를 끼쳤을 때에는 그 정도에 따라 각각변상의 책임을 진다.<br/>
            본 규정은 1994년 1월 1일부터 시행한다.</p>

            <div class="doc-title">포상규정</div>
            <p><strong>제1조(목적)</strong> 회원으로 본회 목적달성에 이바지하였거나 사회에 공헌한 공적이 현저한 자에 대해서 포상함으로써 회원의 명예심과 사기를 진작시키는 데 목적이 있다.</p>
            <p><strong>제2조(포상의 종류)</strong><br/>
            1. 연차표창<br/>
            1) 연차표창은 원칙적으로 당해연도 회장 취임식에서 수여한다.<br/>
            LOM회장 특별표창, 최우수회원상, 우수회원상, 최우수분과위원장상, 우수분과위원장상, 최다수회원확충상, 최우수신입회원상, 우수신입회원상, 최우수부인회원상, 우수부인회원상<br/>
            2. 대외표창<br/>
            본회 발전에 현저한 공로가 있는 대외인사 또는 단체에 대하여 다음 각호와 같이 구분하여 표창한다.<br/>
            1) 대회 인사에 대한 감사패<br/>
            2) 본 회의 사업수행과 관련된 외부 및 기관에 대한 표창<br/>
            3) 본회 운영상 협조가 많았던 단체에 대한 감사패<br/>
            3. 특별표창<br/>
            본 회는 이사회의 의결에 따라 표창할 만한 충분한 공로가 있다고 인정되는 회원, 특우회원에 대하여 수시로 표창할 수 있다.</p>
            <p><strong>제3조 표창의 심사 및 결정</strong><br/>
            1. 연차표창의 심사는 본회의 포상규정 및 사무국의 기록에 의한 심사기준에 의하여 기록표창 분과위원회의 심의를 거쳐 이사회에서 결정한다.<br/>
            2. 대외표창, 특별표창은 당해연도 회장단에서 심의하여 이사회에서 결정한다.<br/>
            3. 사무국장은 6월 및 12월 이사회시 반드시 전 회원에 대하여 포상규정에 의한 총점 및 획득점수가 표시된 자료를 제출 심사를 받아야 한다.</p>
            <p><strong>제4조(설명 및 자료의 제출)</strong><br/>
            포상신청자는 설명 또는 관계증빙자료의 제출을 요구 받았을 경우 이에 응하여야 한다.<br/>
            본 규정은 1991년 1월 1일부터 시행한다.</p>

            <table>
              <tr><th>항목</th><th>점수</th><th>항목</th><th>점수</th></tr>
              <tr><td>총회(임시, 정기)</td><td>15</td><td>회비선납(6개월)</td><td>25</td></tr>
              <tr><td>월례회(5회)</td><td>10</td><td>전국회원대회</td><td>25</td></tr>
              <tr><td>이사회(5회)</td><td>5</td><td>지구회원대회</td><td>25</td></tr>
              <tr><td>분과회(5회)</td><td>10</td><td>한국JC총회</td><td>15</td></tr>
              <tr><td>연수회(자체)</td><td>20</td><td>지구JC총회</td><td>15</td></tr>
              <tr><td>제반사업</td><td>5</td><td>타롬행사</td><td>5</td></tr>
              <tr><td>사무국방문</td><td>1</td><td>형제JC행사</td><td>10</td></tr>
              <tr><td>회비선납(1년)</td><td>50</td><td></td><td></td></tr>
            </table>

            <div class="doc-title">감사규정</div>
            <p><strong>제1조(목적)</strong> 본 규정은 본 회의 업무집행과 재산 상황을 감사하여 합리적이고 능률적인 처리와 정비를 도모함으로써 업무 집행의 완벽을 기함에 그 목적이 있다.</p>
            <p><strong>제2조(감사의 종류)</strong><br/>
            1. 감사의 정기 감사와 특별감사의 2종으로 한다.<br/>
            2. 정기 감사는 회무전반에 대하여 실시한다.<br/>
            3. 특별감사는 특정부분의 회무에 대하여 필요에 따라 실시한다.</p>
            <p><strong>제3조(감사기간)</strong><br/>
            1. 정기 감사는 매년 2회 실시한다.<br/>
            2. 감사는 정기 감사를 실시함에 있어서 감사 실시기간과 감사지침에 관하여 감사실시 10일전까지 회장에게 서면 통보하여야 한다.</p>
            <p><strong>제4조(감사상의 주의)</strong><br/>
            1. 감사를 할 때에는 감사를 받는 임원과 각 기구 및 사무국의 정상적인 활동과 업무를 저해할 수 없다.<br/>
            2. 감사 반원은 감사로 인하여 취득한 사실을 정당한 사유 없이 누설하지 못한다.</p>
            <p><strong>제5조(감사의 협조)</strong> 피 감사자는 감사반이 요구하는 서류의 제출과 그 질문에 대하여 성실한 협조와 답변을 하여야 한다.</p>
            <p><strong>제6조(결과보고)</strong> 감사를 완료한 감사는 지체 없이 그 결과를 서면으로 작성하여 회장을 경유 총회 및 이사회에 보고하여야 한다.<br/>
            본 규정은 1994년 1월 1일부터 시행한다.</p>

            <div class="doc-title">임원선임에 관한 규정</div>
            <h3>제1장 총 칙</h3>
            <p><strong>제1조(목적)</strong> 본 규정은 사단법인 한국청년회의소 산하 새창원청년회의소(이하 '본회'라한다.)의 선거직 임원의 선출과 임명직 임명에 관한 사항을 규정함을 목적으로 한다.</p>
            <p><strong>제2조(선거직 임원)</strong> 전조의 선거직 임원이라 함은 본회의 회장, 부회장 및 감사를 말한다.</p>
            <p><strong>제3조(임명직 임원)</strong> 전 1조의 임명직 임원이라 함은 상임이사, 각 분과위원장을 말한다.</p>
            <p><strong>제4조(선거관리위원회)</strong> 선거직 임원의 선거에 관한 사무를 관리하기 위하여 선거관리위원회(이하 관리위원회라 약칭)를 둔다.</p>

            <h3>제2장 선거관리위원회</h3>
            <p><strong>제5조(구성)</strong><br/>
            1. 선거관리위원회의 위원은 선거관리위원장을 포함 7명 이내로 구성한다.<br/>
            2. 선거관리위원회 위원장은 직전회장이 되며 위원은 정회원 중 이사회 추천 3명과 회장이 이사 중 3명을 지명하여 이사회의 승인을 득하여 임명한다.<br/>
            3. 선거관리위원의 임기는 당해 연도 12월 31일까지로 한다.</p>
            <p><strong>제6조(선거운동)</strong> 선거운동은 회의소 내에서만 행할 수 있다. 단 일반적으로 제한하는 선거운동은 금지한다.</p>
            <p><strong>제7조(직무)</strong><br/>
            1. 선거관리위원장은 선거관리위원회를 대표하며 선거관리위원회의 회무를 총괄하고 총회 이사회에 출석하여 선거에 관한 제반 사무를 보고하고 의견을 진술하여야 한다.<br/>
            2. 선거관리위원장 유고시는 선거관리위원 중에서 회장이 지명하여 이사회의 승인을 받은 위원을 선거관리위원장으로 한다.<br/>
            3. 선거관리위원의 결원이 있을 때에는 전 제5조 2항의 규정에 따라 회장이 보임한다.<br/>
            4. 선거관리위원회의 위원은 선거관리위원장을 보필하고 공정히 선거관리를 하여야 한다.</p>
            <p><strong>제8조(의사)</strong> 선거관리위원회의 의결은 재직위원 과반수 출석과 출석위원 과반수 찬성으로 의결한다. 선거관리위원장은 의결권이 없으며 또 표결 결과가 가부동수인 경우에 그 결정권을 가진다.</p>
            <p><strong>제9조(관리위원회의 임무)</strong> 선거관리위원회는 본 규정에 특별히 정하는 이외에 다음의 업무를 가진다.<br/>
            1. 입후보자의 자격심사<br/>
            2. 선거직 명부의 작성 및 확인<br/>
            3. 총 투표권수의 확정<br/>
            4. 제 13조 1항 1호 및 2호에 정하는 소정약식 결정<br/>
            5. 선거운동 방법 결정<br/>
            6. 선거 공보의 발행<br/>
            7. 투표용지 양식 결정 및 투개표 방법 결정<br/>
            8. 투개표 관리<br/>
            9. 당선자의 확정보고</p>
            <p><strong>제10조(문서발송)</strong> 선거에 관하여 선거관리위원회가 통지하는 사항은 선거관리위원회의 명의로 문서로서 행하여야 한다.</p>
            <p><strong>제11조(임무완료)</strong> 선거관리위원회는 선거사무 처리가 완료되는 즉시 회장에게 선거관리결과 보고서를 제출하여야 한다.</p>
            <p><strong>제12조(선거관리비용)</strong><br/>
            1. 입후보자의 공탁금 중 선거관리위원회가 지출하는 선거관리비용은 선거관리위원회의 결의를 거친 공식적인 제반비용으로 한다.<br/>
            2. 사용된 금액은 선거관리위원회 해산 전에 감사에게 사용내역을 보고하여 감사를 마쳐야한다.</p>

            <h3>제3장 피선거권 및 피임자격</h3>
            <p><strong>제13조(입후보 자격)</strong><br/>
            1. 회장 입후보 자격은 선거권이 있는 정회원 즉 취임 예정일 현재 만3년 이상 재적하고 선거직 임원을 역임한 자로서 정회원 10인 이상의 추천을 받은 자에 한한다.<br/>
            2. 부회장, 감사의 입후보자격은 선거권이 있는 정회원 중 취임 예정일 현재 3년을 재적하고 임명직 임원을 역임한 자로서 정회원 5인 이상의 추천을 받은 자로 한다.</p>
            <p><strong>제14조(자격제한)</strong> 피선거자 또는 피임명자의 본 회에 대한 납입 의무금이 입후보 등록마감일 또는 피임명일 현재 미납되어 있을 경우에는 피선거권 또는 피임명 자격을 인정하지 아니한다.<br/>
            1. 법률상 공민권을 박탈당한 회원은 본 회의 선거직 또는 임명직 임원이 될 수 없다.<br/>
            2. 본 회의 선거직 임원 입후보자는 동일직에 한하여 1회만 입후보 할 수 있다.</p>
            <p><strong>제15조(입후보 등록)</strong> 선거직 임원에 입후보하는 회원은 다음 각 호의 서류를 첨부하여 선거관리위원회에 등록하여야 한다.<br/>
            1. 입후보 등록 신청서 1통<br/>
            2. 입후보 추천서 1통 (정회원의 서명날인)<br/>
            3. 소신서 1통<br/>
            4. 서약서<br/>
            5. JC재직증명서<br/>
            6. 임원연수필 사본<br/>
            7. 등록 공탁금 납부확인서 1통 (재정이사 발행)<br/>
            1) 회장 입후보자는 일금 3,000,000원정을<br/>
            2) 상임부회장 입후보자는 일금 1,500,000원정을<br/>
            3) 내무, 외무부회장 입후보자는 각 일금 1,000,000원정을<br/>
            4) 감사는 각 일금 500,000원정을 공탁하여야 한다.<br/>
            5) 공탁된 금액은 당선자에 한하여 3,000,000원정을 임원선임에 관한 규정에 의하여 선거사무와 관련된 비용에 충당하고 나머지 금액은 새창원청년회의소 회관건립기금 4,500,000원정으로 기탁된다. (단, 선거관리위원회에서는 공탁금 3,000,000원정 내에서 모든 재정을 집행한다.)<br/>
            6) 입후보자가 사퇴한 때 등 어떠한 경우에도 접수 등록된 등록 공탁금은 반환하지 아니한다.<br/>
            7) 추대로 의해 당선된 자의 경우에도 등록 공탁금을 반드시 납부 하여야 한다.</p>
            <p><strong>제16조(입후보자의 등록 확정 공고)</strong> 선거관리위원회는 입후보 등록마감일로부터 10일 이내에 등록 확정된 입후보자의 명단을 정회원에게 서면으로 통보하여야 한다.</p>
            <p><strong>제17조(지명등록)</strong> 후보자 등록이 없을 경우 총회에서 정회원 상호간에 추천하여 후보자 등록을 받는다. 이 경우 단일 후보일 때는 총회 과반수의 승인을 득해야 한다.</p>

            <h3>제4장 투표와 개표</h3>
            <p><strong>제18조(투표와 개표)</strong><br/>
            1. 투표와 개표는 총회에서 실시한다.<br/>
            2. 투표는 무기명 비밀 투표로 한다.<br/>
            3. 투표용지의 개표에 관한 사항은 선거관리위원회가 정하는 바에 따른다.</p>
            <p><strong>제19조(재투표)</strong><br/>
            1. 회장은 투표 결과 최다 득표자가 투표자수의 과반수를 얻지 못하였을 경우에는 차점자와 결선투표를 실시하여야 한다.<br/>
            2. 결선투표에는 다 득표자를 당선자로 한다.</p>

            <h3>제5장 당선자의 결정</h3>
            <p><strong>제20조(당선자의 결정)</strong><br/>
            1. 본 회의 선거직 임원 입후보자는 총회에서 투표자의 과반수를 득표함으로써 당선자가 된다.<br/>
            2. 단일 입후보인 경우에는 총회에서 투표자수의 과반수를 득표하여야 한다.</p>
            <p><strong>제21조(당선자의 발표)</strong> 선거관리위원장은 선거직 임원 당선자가 결정되면 지체 없이 회장에게 보고하여야 하며 회장은 이를 확인한 후 당해 총회에 출석한 정회원에게 확정발표를 하고 동 총회일로 10일 이내에 전 회원에게 통보하여야 한다.</p>
            <p><strong>제22조(일정)</strong><br/>
            1. 선거를 원활히 하기 위하여 다음 각 호의 일정을 정한다.<br/>
            1) 선거관리위원회 구성 : 선거일 30일 전까지<br/>
            2) 선거일 공고 : 선거일 공고일 25일 전까지<br/>
            3) 선거인명부 작성 : 선거일 15일 전까지<br/>
            4) 선거인명부 이의 신청: 선거일 10일 전까지<br/>
            5) 선거인명부 확정통보 : 선거일 9일 전까지<br/>
            6) 입후보 등록 : 선거일 15일 전부터 10일 전까지<br/>
            7) 입후보등록 확정통보 : 선거일 10일 전까지<br/>
            8) 선거공보 제작발송: 선거일 9일 전까지<br/>
            2. 전항의 각 일정에 있어서 개시일 또는 마감일이 공휴일인 경우에는 그 익일로 가산 도는 종료한다.</p>

            <h3>제6장 부 칙</h3>
            <p><strong>제23조(위임규정)</strong> 본 규정에 정하여진 이외의 선거직 임원 선거에 관한 사항은 관리위원회에서 정하는 바에 따른다.<br/>
            본 규정은 1994년 1월 1일부터 시행한다.</p>

            <div class="doc-title">회관건립 및 관리기금규정</div>
            <p><strong>제1조(목적)</strong> 본 규정은 새창원청년회의소 회관건립기금의 조성과 관리 운영의 합리화를 기하는데 목적이 있다.</p>
            <p><strong>제2조(기금조성 및 관리운영)</strong><br/>
            1. 기금의 조성은 다음 항목에 적립한다.<br/>
            1) 선거직 임원 등록금 중 당선자에 해당되는 등록금 450만원과 선거관리비용으로 사용된 후 잔액이 있는 경우 그 금액<br/>
            2) 신입회원가입금 중 일부 (이사회 의결)<br/>
            3) 특별기부금 및 찬조금<br/>
            4) 기타 수입<br/>
            2. 기금의 조성은 상기 각 항 발생시와 동시에 기금 구좌에 입금되어야 한다.<br/>
            3. 본 기금은 타 용도로 변경 사용할 수 없다.</p>
            <p><strong>제3조(회관건립 기금관리위원회 구성 및 운용)</strong><br/>
            1. 본 위원회 구성은 위원장과 위원으로 구성한다.<br/>
            2. 위원장은 직전회장이 되며 위원은 이사회의 추천으로 5명 이내로 회장이 임명한다. (역대회장은 당연직 임원)<br/>
            3. 기금의 운용은 위원회 의결을 거쳐 총회 결의로써 행한다.</p>
            <p><strong>제4조(관리)</strong><br/>
            1. 위원장은 기금의 장부 및 회의록을 작성하여 사무국에 비치하여야 한다.<br/>
            2. 전항 규정에 의한 장부와 기록문서는 영구 보존한다.</p>
            <p><strong>제5조(회의)</strong> 위원회는 매 분기 마다 1회 이상 개최한다.</p>

            <div class="doc-title">회원경조규정</div>
            <p><strong>제1조(목적)</strong> 본 회 상호간 우의를 증진시키기 위하여 아래와 같이 경조 규정을 둔다.</p>
            <p><strong>제2조(대상)</strong> 경조는 본회의 회원 및 특우회원과 그 배우자, 부모, 자녀를 대상으로 한다.<br/>
            1. 경사의 범위는 다음과 같다.<br/>
            1) 회원의 결혼 2) 회원의 자녀 돌 3) 회원의 부모 칠순 4) 회원의 개업 및 이전확장 입택 5) 회원의 전역<br/>
            2. 조사범위는 다음과 같다.<br/>
            1) 회원의 사망 및 부인회원의 사망<br/>
            2) 회원 및 부인회원의 자녀 및 부모 사망<br/>
            3) 회원의 조부모 사망<br/>
            4) 특우회원 및 배우자의 부모, 자녀사망<br/>
            3. 기타 회장단 회의에서 필요하다고 인정하는 사항도 경조사 대상으로 한다.</p>
            <p><strong>제3조(방법)</strong><br/>
            1. 경조사는 현금 지급을 원칙으로 하되 기념품등 물품으로도 대신 할 수 있다.<br/>
            2. 경조금의 지급은 원칙적으로 별표의 규정에 따른다.<br/>
            3. 제2조 2항 1호의 경우에는 JC장으로 할 수 있다.</p>
            <p><strong>제4조(통보)</strong><br/>
            1. 회원은 상조를 요하는 사항이 발생된 즉시 직접 또는 간접으로 본 회의소 사무국에 통보하여야 한다.<br/>
            2. 사무국장은 경조사항 발생 통보를 접수 받은 즉시 서면 또는 구두로 전 회원에게 통보하여야 한다.<br/>
            3. 경조사항을 사전에 사무국에 통보치 않을 시는 본 경조규정을 적용할 수 없다.</p>
            <p><strong>제5조(경조비 납입 및 관리)</strong><br/>
            1. 회원은 매년 1월 30일까지 이사회에서 정하는 경조 예납금을 사무국에 납입하여야 하며 신입회원 가입 시 납부한다.<br/>
            2. 경조 예납금 초과 시는 수시로 경조규정 분담금을 징수한다.<br/>
            3. 경조사비의 지급은 회의소내의 제외분담금을 납부한 회원에 한한다.(단, 이후에 회비를 납부할 경우 미지급된 경조사비를 재지급한다.)</p>
            <p><strong>제6조</strong> 이 규칙은 공포된 날로부터 시행한다.</p>
            
            <h4>&lt;별 표&gt;</h4>
            <table>
              <tr><th>구분</th><th>항목별</th><th>지급기준</th></tr>
              <tr><td rowspan="3">경사</td><td>1. 당사자 결혼</td><td>현금 500,000원, 화환 3단</td></tr>
              <tr><td>2. 자녀의 돌</td><td>현금 200,000원</td></tr>
              <tr><td>3. 개업 및 이전, 확장, 입택</td><td>화분</td></tr>
              <tr><td rowspan="4">조사</td><td>1. 회원 및 부인회원의 사망</td><td>현금(회원수×10,000원), 근조 3단 포함</td></tr>
              <tr><td>2. 회원, 부인회원의 자녀 및 부모사망</td><td>현금(회원수×5,000원), 근조 3단 포함</td></tr>
              <tr><td>3. 회원의 조부모 사망</td><td>근조 3단</td></tr>
              <tr><td>4. 특우회원 및 배우자의 부모 자녀 사망</td><td>현금(회원수×5,000원), 근조 3단 포함</td></tr>
              <tr><td>기타</td><td>경·조사 항목에는 없으나 특별한 경우가 발생시</td><td>현금, 물품, 생화<br/>-회장단 회의 시 결정지급 사후보고</td></tr>
            </table>

            <div class="doc-title">소청심사위원회 운영규정</div>
            <p><strong>제1조(목적)</strong> 본 규정은 새창원청년회의소(이하 본회라 칭한다) 정관 제 17조 규정에 따라 소청심사위원회 (이하 위원회라 칭한다)의 원활한 운영을 기함을 목적으로 한다.</p>
            <p><strong>제2조(구성)</strong> 위원회는 위원장 1인, 부위원장 1인, 약간의 위원으로 구성하되 그 총수가 7인 이내이어야 한다.<br/>
            1. 위원장 및 부위원장은 본 회 선거직 임원중에서 회장이 임명한다.<br/>
            2. 위원은 본회의 선거직 임원이나 임명직 임원이상 역임자 중에서 회장이 임명하는 전 회원 5인 이내로 하며 특우회장은 당연직 위원으로 위촉한다.</p>
            <p><strong>제3조(심의)</strong> 위원회는 다음 각호의 사항의 심의 의결하여 총회 및 이사회에 의안상정 여부를 결정한다.<br/>
            1. 정관 및 규정에 대한 유권해석 요청<br/>
            2. 회원의 권리관계 청원 요청<br/>
            3. 총회, 월례회, 이사회 결정 심사에 대한 이의 제기<br/>
            4. 지구 및 중앙 소청위원회 유권해석 요청</p>
            <p><strong>제4조(소청심사청구)</strong><br/>
            1. 회원이 소청심사를 청구한 때에는 다음 각 호의 사항을 기재한 소청심사 청구서를 위원회에 제출하여야 한다.<br/>
            1) 주소, 성명, JC직위, 생년월일, 회원증번호<br/>
            2) 소청의 이유서<br/>
            3) 당해 년도 회비 납부 완납 영수증<br/>
            4) 기타 입증자료<br/>
            5) 징계요구 및 처분자가 징계의결 또는 소청의결이 경하다고 위원회에 심사를 청구할 때에도 상기 1항을 준한다.</p>
            <p><strong>제5조(소청심사청구기한)</strong> 소청심사 청구기한은 징계처분 심의 결정을 받은 날로부터 25일 이내로 둔다.</p>
            <p><strong>제6조(소청심사 소집)</strong> 소청심사 위원회는 심사청구를 받은 날로부터 30일 이내 소집 개최하여야 한다. 다만, 심사청구사유 이유가 없을 때에는 이유서를 작성 첨부하여 기각할 수 있다.</p>
            <p><strong>제7조(기일지정 통지)</strong> 위원회가 소청 건에 대하여 심사를 할 때에는 소청인에게 심사일시, 장소 등을 3일전에 통지하여 출석할 수 있도록 하여야 한다.</p>
            <p><strong>제8조(의결)</strong><br/>
            1. 위원회는 2/3이상의 출석과 출석위원 과반수의 찬성으로 심의 의결하되 가부동수인 경우에는 위원장의 결정에 따른다.<br/>
            2. 소청심사 의결방법은 비밀투표로 함을 원칙으로 한다.</p>
            <p><strong>제9조(진술권)</strong> 위원회는 출석한 당사자의 진술을 청취하여야 하며, 필요시에는 구술로 심문할 수 있다.</p>
            <p><strong>제10조(심사의 범위)</strong><br/>
            1. 위원회는 정관 제 16조 1항 각호의 징계양정 범위 내에서 정상을 참작하여 징계처분 사항을 경하게 또는 중하게 의결할 수 있다.<br/>
            2. 위원회는 징계 또는 소청의 원인이 된 사실 외는 심의하지 못한다.</p>
            <p><strong>제11조(결정서 작성)</strong> 위원회가 소청심사 청구 건에 대하여 결정을 할 때에는 다음 각호의 사항을 기재한 소청심사결정서를 작성하고 출석위원 2인 이상의 서명날인을 받아 기록 보존한다.<br/>
            1) 소청자 인적사항 2) 결정주문 3) 결정 이유의 개요 4) 기타 증거 및 판단자료</p>
            <p><strong>제12조(결정서의 송부 및 최종의결)</strong><br/>
            위원회는 소청심사 결정서를 작성하여 최종의결 기관인 총회 또는 이사회에 상정하여야 한다.<br/>
            (총회 및 이사회는 재적회원 과반수의 출석과 출석회원 2/3이상의 찬성으로 의결하며 찬반토론 없이 비밀투표함을 원칙으로 한다.)</p>
            <p><strong>제13조(기타)</strong><br/>
            1. 소청심사 결정사항에 대하여는 본 위원회에 재심을 청구할 수 없다. (단, 이의가 있을 시 지구 및 중앙 소청심사위원회에 유권해석을 요청할 수 있다.)<br/>
            2. 위원회에 접수 계류 중인 소청심사 서류에 한하여 청구자의 원에 따라 반환할 수 있다.<br/>
            본 규정은 1999년 1월 1일부터 시행한다.</p>

            <div class="doc-title">포상에 관한 규정</div>
            <p><strong>제1조(목적)</strong> 이 규정은 새창원청년회의소에서 행하는 포상의 기준과 절차에 필요한 사항을 규정함을 목적으로 한다.</p>
            <p><strong>제2조(포상대상)</strong> 이 규정에 따른 포상은 새창원청년회의소 발전에 공헌한 회원, 시민, 학생(외국인을 포함한다. 이하 같다) 및 단체에 행한다.</p>
            <p><strong>제3조(포상권자)</strong> 포상은 회장이 행한다.</p>
            <p><strong>제4조(포상의 종류)</strong> 이 규정에 따른 포상은 표창장, 감사장, 상장으로 나누어 시행한다.</p>
            <p><strong>제5조(표창장)</strong> 표창장은 다음 경우에 수여한다.<br/>
            1. 최우수 및 우수분과위원장은 당해 분과사업의 계획과 시행이 일치 수행되어야 한며 새창원청년회의소 발전에 기여한 공적이 현저한 경우<br/>
            2. 최우수회원상 및 우수회원상은 이사를 역임하였거나 역임하고 있는 회원으로서 소정의 활동 기준을 수료하여 새창원청년회의소에 기여한 공적이 현저한 경우<br/>
            3. 최우수신입회원상 및 우수신입회원상은 입회하여 6개월 이상 경과하고 이사를 역임하지 않은 회원으로서 소정의 활동기준을 수료하여 새창원청년회의소 발전에 공적이 현저한 경우<br/>
            4. 최우수부인회원상 및 우수부인회원상은 새창원청년회의소 부인회의 규정을 준수한자로서 부인회장의 추천자로 한다.<br/>
            5. 특별공로패는 한국JC, 지구JC에 상신하는 상을 말하며 본회 발전에 기여한 자로 승점 표에 관계 없이 기록표창위원회에서 상신 할 수 있다.</p>
            <p><strong>제6조(감사장)</strong> 감사장은 새창원청년회의소의 사업수행에 적극 협조하거나 대외적으로 새창원청년회의소 의 명예를 높이 선양시킨 개인이나 단체에 수여한다.</p>
            <p><strong>제7조(상장)</strong> 상장은 다음 각호의 경우에 수여한다.<br/>
            1. 각종 품평회, 경진회, 전시회 등에 입선한 경우<br/>
            2. 학술, 예술, 체육 기타 경기대회에서 우수한 성적을 나타낸 경우<br/>
            3. 각종 교육 성적이 특히 우수한 경우</p>
            <p><strong>제8조(포상 방법 및 부상)</strong><br/>
            1. 포상은 별지 제1호 내지 제3호 서식에 따른다.<br/>
            2. 전항의 포상장은 상금, 상패, 기타 부상과 함께 수여할 수 있다.<br/>
            3. 점수는 실시한 다음날부터 다음해 이월 계산한다.</p>
            <p><strong>제9조(포상절차)</strong> 제5조와 제6조의 규정에 따른 포상예정일 15일전에 심사위원회에 제출하여 시상자를 선정하고 이사회에 결의를 거쳐서 수여하여야 한다.</p>
            <p><strong>제10조(포상시기)</strong> 포상은 정기적으로 시행함을 원칙으로 한다. 다만, 필요한 경우에는 수시로 행할 수 있다.</p>
            <p><strong>제11조(포상대상의 등재)</strong> 이 규정에 따른 포상은 별지 제5호 서식의 포상대장에 등재하여야 한다.</p>
            <p><strong>제12조(시행세칙)</strong> 이 규정 시행에 관하여 필요한 사항은 시행세칙으로 한다.<br/>
            이 규정은 2000년 3월 10일 개정하고 2000년 1월 1일부터 소급하여 시행한다.</p>

            <h4>(별지 제1호 서식)</h4>
            <div class="border border-gray-300 p-4 bg-gray-50 text-center mb-6">
              제 호<br/><br/><strong class="text-xl">표 창 장</strong><br/><br/>
              소 또는 소속<br/>성명<br/><br/>(표창문)<br/><br/>년 월 일<br/><br/>새창원청년회의소 회장 ○○○(인)
            </div>

            <h4>(별지 제2호 서식)</h4>
            <div class="border border-gray-300 p-4 bg-gray-50 text-center mb-6">
              제 호<br/><br/><strong class="text-xl">감 사 장</strong><br/><br/>
              주소 또는 소속<br/>성명<br/><br/>(감사문)<br/><br/>년 월 일<br/><br/>새창원청년회의소 회장 ○○○(인)
            </div>

            <h4>(별지 제3호 서식)</h4>
            <div class="border border-gray-300 p-4 bg-gray-50 text-center mb-6">
              제 호<br/><br/><strong class="text-xl">상 장</strong><br/><br/>
              주소 또는 소속<br/>성명<br/><br/>(상 문)<br/><br/>년 월 일<br/><br/>새창원청년회의소 회장 ○○○(인)
            </div>

            <h4>(별지 제4호 서식)</h4>
            <table>
              <tr><th colspan="4">적 공 서 조</th></tr>
              <tr><td>(1)본적</td><td></td><td>(2)주소</td><td></td></tr>
              <tr><td>(3)성명</td><td></td><td>(4)생년월일</td><td></td></tr>
              <tr><td>(5)가입년월일</td><td></td><td>(6)추천서열</td><td></td></tr>
              <tr><th colspan="4">과거포상기록(훈장 포장 표창)</th></tr>
              <tr><td>(7)년월일</td><td>(8)내용</td><td>(9)년월일</td><td>(10)내용</td></tr>
              <tr><th colspan="4">점 표</th></tr>
              <tr><td>(11)내역</td><td></td><td>(12)총승점</td><td>(13)비고</td></tr>
              <tr><th colspan="4">조 사 자</th></tr>
              <tr><td>(14)직책</td><td></td><td>(15)성명</td><td></td></tr>
              <tr><td colspan="4">제반 기록이 상위 없음을 확인함<br/><br/>20 년 월 일<br/><br/>직위 기록표창분과위원장 성명 ○○○(인)</td></tr>
            </table>

            <h4>(별지 제5호 서식) 포상대 장</h4>
            <table>
              <tr><th>호수</th><th>포상년월일</th><th>포상 종별</th><th>소속 또는 주소</th><th>피포상자 성별</th><th>성명</th><th>공적개요</th><th>기념품 또는 부상</th><th>참고</th></tr>
              <tr><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td><td></td></tr>
            </table>

            <div class="doc-title">포상에 관한규정시행규칙</div>
            <p><strong>제정 (1981.8.2)</strong></p>
            <p><strong>제1조(목적)</strong> 본 규정은 새창원청년회의소(이하 본회라 칭한다) 포상의 기준과 절차에 필요한 사항을 목적으로 한다.</p>
            <p><strong>제2조(사무주관)</strong> 포상에 관하여는 기록표창분과위원장이 관장하나 모든 행정사무처리는 사무국에서 실시한다.</p>
            <p><strong>제3조(용어의 정의)</strong><br/>
            1) 규정 제5조 각항에 규정한 소정의 활동기준이라 함은 필수적으로 수행하여야 할 회원의 임무로서 별첨 제1호 내지 제3호 승점표에 기록된 내용을 말한다.<br/>
            2) 규정 제9조에 규정한 심사위원회이라 함은 회장, 부회장, 담당분과 위원장, 경험이 많은 회원 2명 (단, 회장 및 부회장, 사무국장을 역임한자) 등 5명을 말한다.</p>
            <p><strong>제4조(부상)</strong> 제8조에 따른 부상 중 상패는 따로 정한다.</p>
            <p><strong>제5조(포상의 시기)</strong> 규정 제10조에 다른 정기포상은 창립행사 및 이·취임식시에 실시한다.<br/>
            이 규칙은 2000년 3월 10일 개정하고 2000년 1월 1일부터 소급하여 실시한다.</p>

            <h4>(별첨 제1호 승점표) 분과위원회상 승점표</h4>
            <table>
              <tr><th colspan="5">1. 승 점</th></tr>
              <tr><th>순위</th><th colspan="2">내 용</th><th>점수</th><th>비고</th></tr>
              <tr><td>1</td><td colspan="2">타당성 분과 사업계획의</td><td>30</td><td></td></tr>
              <tr><td>2</td><td colspan="2">분과 사업시행의 수행 및 성공여부</td><td>20</td><td></td></tr>
              <tr><td rowspan="4">3</td><td colspan="2">분과 위원회의 운영상태</td><td>15</td><td></td></tr>
              <tr><td colspan="2">(1) 월1회 개최 시</td><td>10</td><td></td></tr>
              <tr><td colspan="2">(2) 분기 1회 개최 시</td><td></td><td></td></tr>
              <tr><td colspan="2">(3) 반기 1회 개최 시</td><td>5</td><td></td></tr>
              <tr><td>4</td><td colspan="2">이사회에 분과위원회에 참관 시</td><td>10</td><td></td></tr>
              <tr><td>5</td><td colspan="2">계획된 사업을 완료하였을 경우</td><td>10</td><td></td></tr>
              <tr><td colspan="3" class="text-right font-bold">계 소</td><td></td><td></td></tr>
              <tr><th colspan="5" class="bg-red-50">2. 감 점</th></tr>
              <tr><td class="bg-red-50 text-red-600">1</td><td colspan="2" class="bg-red-50 text-red-600">사업을 미수행시 계획된</td><td class="bg-red-50 text-red-600">30</td><td class="bg-red-50 text-red-600"></td></tr>
              <tr><td colspan="3" class="text-right font-bold bg-red-50">계 소</td><td class="bg-red-50"></td><td class="bg-red-50"></td></tr>
              <tr><th colspan="3" class="text-right text-blue-800">3. 총 점(1)-(2)</th><th></th><th></th></tr>
            </table>

            <h4>(별첨 제2호 승점표) 우수회원상 승점표</h4>
            <table>
              <tr><th colspan="4">1. 승 점</th></tr>
              <tr><th>순위</th><th>내 용</th><th>점수</th><th>비고</th></tr>
              <tr><td>1</td><td>월례회참석(100%=50, 90%=45, 80%=40, 75%=35)</td><td>+5</td><td></td></tr>
              <tr><td>2</td><td>한국제이씨 행사 참여</td><td>10</td><td>부인회원</td></tr>
              <tr><td>3</td><td>지구제이씨 행사 참여</td><td>10</td><td>동반 시+5</td></tr>
              <tr><td>4</td><td>국제 모임에 참여</td><td>10</td><td>매1회</td></tr>
              <tr><td>5</td><td>타찹타행사 참여</td><td>10</td><td></td></tr>
              <tr><td>6</td><td>한국 제이씨 연수원 수료</td><td>20</td><td></td></tr>
              <tr><td>7</td><td>회원 및 신입회원 교육 참여시</td><td>10</td><td></td></tr>
              <tr><td>8</td><td>케이 제이씨 뉴스에 투고 기재 시</td><td>10</td><td></td></tr>
              <tr><td>9</td><td>회원 댁 길흉사 참여시(사무국에서 공식방문)</td><td>5</td><td></td></tr>
              <tr><td>10</td><td>계획된 사업을 완료하였을 경우</td><td>15</td><td></td></tr>
              <tr><td>11</td><td>각종 사업수행에 참여시</td><td>5</td><td></td></tr>
              <tr><td>12</td><td>신입회원 1명 이상 추천 가입 시</td><td>15</td><td>1명당</td></tr>
              <tr><td>13</td><td>월례회 중 세미나 연사를 했을 경우</td><td>15</td><td>매1회</td></tr>
              <tr><td>14</td><td>행사 차량 지원 시 매1회(타 도시로 갈 때)</td><td>10</td><td></td></tr>
              <tr><td colspan="2" class="text-right font-bold">소 계</td><td></td><td></td></tr>
              <tr><th colspan="4" class="bg-red-50">2. 감 점</th></tr>
              <tr><td class="bg-red-50 text-red-600">1</td><td class="bg-red-50 text-red-600">당월에 회비 미납 시</td><td class="bg-red-50 text-red-600">-5</td><td class="bg-red-50 text-red-600">매1회</td></tr>
              <tr><td class="bg-red-50 text-red-600">2</td><td class="bg-red-50 text-red-600">월회 및 총회에 정장을 하지 않았을 경우</td><td class="bg-red-50 text-red-600">-3</td><td class="bg-red-50 text-red-600"></td></tr>
              <tr><td class="bg-red-50 text-red-600">3</td><td class="bg-red-50 text-red-600">결석했을 경우 이사회</td><td class="bg-red-50 text-red-600">-5</td><td class="bg-red-50 text-red-600"></td></tr>
              <tr><td class="bg-red-50 text-red-600">4</td><td class="bg-red-50 text-red-600">지각 및 조퇴했을 경우 이사회</td><td class="bg-red-50 text-red-600">-2</td><td class="bg-red-50 text-red-600"></td></tr>
              <tr><td colspan="2" class="text-right font-bold bg-red-50">소 계</td><td class="bg-red-50"></td><td class="bg-red-50"></td></tr>
              <tr><th colspan="2" class="text-right text-blue-800">3. 총 점(1)-(2)</th><th></th><th></th></tr>
            </table>

            <h4>(별첨 제3호 승점표) 모범회원상 승점표</h4>
            <table>
              <tr><th colspan="4">1. 승 점</th></tr>
              <tr><th>순위</th><th>내 용</th><th>점수</th><th>비고</th></tr>
              <tr><td>1</td><td>월례회 참석(100%=50, 90%=45, 80%=40, 75%=35)</td><td>+5</td><td></td></tr>
              <tr><td>2</td><td>한국제이씨 행사 참여</td><td>10</td><td>내용란을</td></tr>
              <tr><td>3</td><td>지구제이씨 행사 참여</td><td>10</td><td>참조</td></tr>
              <tr><td>4</td><td>국제 모임에 참여</td><td>10</td><td>부인회원</td></tr>
              <tr><td>5</td><td>한국제이씨 연수원 수료</td><td>10</td><td>동반 시+5</td></tr>
              <tr><td>6</td><td>신입회원 교육 시 참가</td><td>10</td><td>매1회</td></tr>
              <tr><td>7</td><td>케이 제이씨 뉴스에 투고 게재 시</td><td>10</td><td></td></tr>
              <tr><td>8</td><td>타 참타 행사 참여</td><td>5</td><td></td></tr>
              <tr><td>9</td><td>월례회중 세미나 연사를 했을 경우</td><td>10</td><td></td></tr>
              <tr><td>10</td><td>이사회 참관 시</td><td>5</td><td></td></tr>
              <tr><td>11</td><td>회원 댁 길흉사 참여시(사무국에서 공식방문)</td><td>5</td><td></td></tr>
              <tr><td>12</td><td>신입회원 1명이상 추천 가입 시</td><td>15</td><td>44</td></tr>
              <tr><td>13</td><td>사업수행에 참여시 각종</td><td>10</td><td>1명당</td></tr>
              <tr><td>14</td><td>행사 차량 지원 시(타 도시로 갈 때)</td><td>5</td><td>매1회</td></tr>
              <tr><td>15</td><td>선납제=1년을 4/4분기로 나누어서 분기 첫 달 분기 말일까지 선납 에서</td><td>20</td><td></td></tr>
              <tr><td colspan="2" class="text-right font-bold">소 계</td><td></td><td></td></tr>
              <tr><th colspan="4" class="bg-red-50">2. 감 점</th></tr>
              <tr><td class="bg-red-50 text-red-600">1</td><td class="bg-red-50 text-red-600">당월에 회비 미납 시</td><td class="bg-red-50 text-red-600">-5</td><td class="bg-red-50 text-red-600"></td></tr>
              <tr><td class="bg-red-50 text-red-600">2</td><td class="bg-red-50 text-red-600">총회에 정장을 하지 않았을 경우 월회</td><td class="bg-red-50 text-red-600">-3</td><td class="bg-red-50 text-red-600"></td></tr>
              <tr><td colspan="2" class="text-right font-bold bg-red-50">소 계</td><td class="bg-red-50"></td><td class="bg-red-50"></td></tr>
              <tr><th colspan="2" class="text-right text-blue-800">3. 총 점(1)-(2)</th><th></th><th></th></tr>
            </table>

            <div class="doc-title">문서기록 보관, 보존규정</div>
            <p><strong>제정(2000.3.10)</strong></p>
            <h3>제1장 총 칙</h3>
            <p><strong>제1조(목적)</strong> 본 규정은 편철 및 보관, 보존의 방법과 절차를 정하여 문서처리의 신속과 정확을 기함을 목적으로 한다.</p>
            <p><strong>제2조(적용범위)</strong> 새창원청년회의소 모든 문서의 편철, 보관, 보존은 한국청년회의소의 특별한 규정이 있는 것을 제외하고는 본 규정에 정하는 바에 의한다.</p>
            <p><strong>제3조(정의)</strong> 본 규정에 사용하는 용어의 정의는 다음과 같다.<br/>
            1) "보관"이라 함은 문서의 처리 완결 후부터 보존되기 전까지의 관리를 말한다.<br/>
            2) "보존"이라 함은 보관이 끝난 문서를 소정의 보존기간에 따라 관리하는 것을 말한다.</p>
            <p><strong>제4조(보존기간)</strong> 문서의 보존기간은 다음 5종으로 구분한다.<br/>
            1) 영구보존 원본을 영구히 보존할 문서<br/>
            2) 준영구보존- 영구보존할 필요는 없으나 10년 이상을 보존할 문서로서 개개문건의 성질에 따라 특정 기간을 정할 문서<br/>
            ① 10년 보존 ② 5년 보존 ③ 3년 보존 ④ 1년 보존</p>
            <p><strong>제5조(보존기간의 변경)</strong> 문서관리 보존책임자는 매분기말 전조의 규정에 의하여 보존기간을 연장, 단축할 필요가 있을 때에는 본회의소 의장의 승인을 얻어 그 기간을 연장, 단축한다.</p>
            <p><strong>제6조(기간)</strong> 보존기간은 처리완결의 익년 1월 1일부터 기산한다.</p>

            <h3>제2장 편철, 보관</h3>
            <p><strong>제7조(분류)</strong> 처리 완결된 문서는 기능별 10분류 방법에 따라 분류한다.</p>
            <p><strong>제8조(1건철)</strong> 문서는 매 안건마다 그 발생, 경과 및 완결에 관계되는 문서를 일괄하여 발생순으로 표지를 사용하여 1건으로 합철한다.</p>
            <p><strong>제9조(보관철의 사용)</strong><br/>
            1) 1건철이 된 문서를 보관할 때에는 별지 제1호 서식에 의한 보관철(출다)를 사용한다.<br/>
            2) 보관철 내의 문서량은 200매를 기준함을 원칙으로 한다.</p>
            <p><strong>제10조(편철방법)</strong> 완결된 1건문서는 보관철 조견표가 있는 면에 완결 일자 순으로 최근 문서가 상부에 오도록 철하고 그 반대 면에 색인목록에 붙인다.</p>
            <p><strong>제11조(색인목록)</strong> 색인목록에는 최종 1건문서의 대표적 완결문서건명을 기재한다.</p>
            <p><strong>제12조(장수표시)</strong> 보관철 내의 장수표시는 하부한계선 좌측에 기입한다.</p>

            <h3>제3장 보 존</h3>
            <p><strong>제13조(보존)</strong> 모든 보관철은 연도별, 분류번호별, 보존기간별로 보존하여야 한다.</p>
            <p><strong>제14조(보존문서 기록대장)</strong> 보존되는 보관철의 현황을 파악하기 위하여 별지 제2호 서식에 의한 보존 문서 기록대장에 보존기간별로 현황을 기록하여 비치하여야 한다.</p>
            <p><strong>제15조(점검 및 소독)</strong> 관리전담자 또는 관리담당자는 년1회 이상 보존 문서 기록대장과 보존 문서를 대조하여 보존상태를 확인하여야 하며 보존문서의 변질, 충해 등을 방지하기 위하여 소독을 실시하여야 한다.</p>
            <p><strong>제16조</strong> 회계연도말 결산보고 감사 후 문서는 이관을 통해 보관 (각 분과별)</p>

            <h3>제4장 폐 기</h3>
            <p><strong>제17조(폐기결정)</strong> 문서를 폐기 결정할 때는 처리완결을 확인하고 문서대장의 완결란에 폐기 결정일자를 기입한 후 폐기 절차를 밟는다.</p>
            <p><strong>제18조(보존기간 경과문서의 폐기)</strong> 보존기간이 끝난 문서는 보존문서의 기록대장에 홍색글씨로 폐기 일자를 기입한 후 폐기하여야 한다.</p>
            <p><strong>제19조(재생)</strong> 폐기문서는 특별한 경우를 제외하고는 소각하지 않고 재생 활용할 수 있도록 한다.</p>
            <p><strong>제20조(시행세칙)</strong> 본 규정 시행에 관하여 필요한 사항은 시행세칙으로 정한다.<br/>
            이 규정은 제정한 날로부터 시행한다.</p>

            <h4>[별표] 총 기</h4>
            <table>
              <tr><th>분류번호</th><th>기능명칭</th><th>세부기능</th><th>기능종별</th><th>보존기간</th></tr>
              <tr><td rowspan="7">101</td><td rowspan="7">사무국</td><td rowspan="2">문서</td><td>문서접수부</td><td>1년</td></tr>
              <tr><td>문서발송부</td><td>1년</td></tr>
              <tr><td rowspan="2">회계</td><td>수납부</td><td>1년</td></tr>
              <tr><td>기금대장</td><td>영구</td></tr>
              <tr><td rowspan="2">일지</td><td>사무국 일지</td><td>1년</td></tr>
              <tr><td>도서목록</td><td>영구</td></tr>
              <tr><td>회원명단</td><td>신입회원 가입추천서철</td><td>영구</td></tr>
              <tr><td rowspan="5">110</td><td rowspan="5">기록표창분과</td><td rowspan="2">회의록</td><td>이사 회의록</td><td>영구</td></tr>
              <tr><td>총회 및 임시총회 회의록</td><td>영구</td></tr>
              <tr><td>화보</td><td>역대화보</td><td>영구</td></tr>
              <tr><td>표창</td><td>표창 기록부</td><td>영구</td></tr>
              <tr><td>문서</td><td>보존문서 기록대장</td><td>영구</td></tr>
            </table>

            <button onclick="window.scrollTo({top:0, behavior:'smooth'})" class="fixed bottom-6 right-6 w-12 h-12 bg-gray-900 text-white rounded-full shadow-lg flex items-center justify-center opacity-70 hover:opacity-100 z-30 transition font-black">↑</button>
          </div>
        `;
      }
    }

    function renderModal() {
      const item = state.selectedItem;
      const isPast = state.modalType === 'past';
      
      return `
        <div class="fixed inset-0 bg-black/60 z-50 flex flex-col justify-end transition-opacity backdrop-blur-sm" onclick="closeModal()">
          <div class="bg-white w-full rounded-t-3xl p-6 pb-8 max-h-[95vh] overflow-y-auto" onclick="event.stopPropagation()">
            <div class="flex justify-between items-start mb-5">
              <div class="flex-1"></div>
              <div class="flex space-x-2 shrink-0">
                ${state.userRole === 'admin' ? `<button onclick="startEditItem()" class="bg-gray-100 text-gray-700 px-4 py-2 rounded-xl text-sm font-black hover:bg-gray-200">수정</button>` : ''}
                <button onclick="closeModal()" class="bg-gray-100 text-gray-700 px-4 py-2 rounded-xl text-sm font-black hover:bg-red-50 hover:text-red-600">닫기</button>
              </div>
            </div>
            
            <div class="flex flex-col items-center">
              <div class="w-32 h-32 bg-gray-100 rounded-full flex items-center justify-center text-gray-400 overflow-hidden mb-4 shadow-md border-4 border-white ring-2 ring-gray-100">
                ${item.imgUrl ? `<img src="${item.imgUrl}" class="w-full h-full object-cover"/>` : `<svg class="w-14 h-14" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd"></path></svg>`}
              </div>
              <h2 class="text-2xl font-black text-gray-900">${item.name}</h2>
              <p class="text-blue-800 font-black mt-2 bg-blue-50 border border-blue-100 px-3 py-1 rounded-lg">${isPast ? `${item.generation}대 ${state.pastTab === 'lom' ? '회장' : '특우회장'}` : (item.role || '새창원청년회의소 회원')}</p>
            </div>

            <div class="bg-gray-50 rounded-2xl p-5 mt-6 space-y-4 border border-gray-100">
              <div class="flex items-center"><div class="w-1/3 text-sm text-gray-500 font-bold">연락처</div><div class="w-2/3 font-black text-gray-900">${item.phone || '-'}</div></div>
              <div class="flex items-center"><div class="w-1/3 text-sm text-gray-500 font-bold">직장명</div><div class="w-2/3 font-black text-gray-900">${item.company || '-'}</div></div>
              ${!isPast && item.type === 'regular' ? `<div class="flex items-center"><div class="w-1/3 text-sm text-gray-500 font-bold">입회연도</div><div class="w-2/3 font-black text-gray-900">${item.joinYear || '-'}년</div></div>` : ''}
            </div>

            ${state.userRole === 'admin' ? `
              <div class="mt-6 border-t border-gray-100 pt-5">
                <h4 class="text-xs font-black text-gray-400 mb-3 uppercase tracking-wider flex items-center"><span class="mr-1">📋</span> 소속 및 직책 관리 (포괄 이동)</h4>
                <div class="grid grid-cols-2 gap-2">
                  ${item.type !== 'regular' ? `<button onclick="initiateTransfer('regular')" class="py-3 bg-blue-50 text-blue-700 rounded-xl text-xs font-black border border-blue-100 hover:bg-blue-100 transition shadow-sm">➡ 정회원으로 이동</button>` : ''}
                  ${item.type !== 'special' ? `<button onclick="initiateTransfer('special')" class="py-3 bg-purple-50 text-purple-700 rounded-xl text-xs font-black border border-purple-100 hover:bg-purple-100 transition shadow-sm">➡ 특우회원으로 이동</button>` : ''}
                  <button onclick="initiateTransfer('pastLom')" class="py-3 bg-amber-50 text-amber-700 rounded-xl text-xs font-black border border-amber-100 hover:bg-amber-100 transition shadow-sm">➕ 역대회장 등록</button>
                  <button onclick="initiateTransfer('pastSpecial')" class="py-3 bg-teal-50 text-teal-700 rounded-xl text-xs font-black border border-teal-100 hover:bg-teal-100 transition shadow-sm">➕ 역대 특우회장 등록</button>
                </div>
              </div>
            ` : ''}

            <div class="flex space-x-3 mt-6 border-t border-gray-100 pt-5">
              <a href="tel:${item.phone || '#'}" class="flex-1 ${item.phone ? 'bg-green-500 hover:bg-green-600 shadow-md transform hover:-translate-y-0.5' : 'bg-gray-200 text-gray-400 pointer-events-none'} text-white py-4 rounded-xl font-bold flex flex-col items-center justify-center transition-all">
                <span class="text-xl mb-1">📞</span><span class="text-[11px] font-black tracking-wide">전화걸기</span>
              </a>
              <a href="sms:${item.phone || '#'}" class="flex-1 ${item.phone ? 'bg-blue-500 hover:bg-blue-600 shadow-md transform hover:-translate-y-0.5' : 'bg-gray-200 text-gray-400 pointer-events-none'} text-white py-4 rounded-xl font-bold flex flex-col items-center justify-center transition-all">
                <span class="text-xl mb-1">💬</span><span class="text-[11px] font-black tracking-wide">문자전송</span>
              </a>
              <button onclick="exportVCard('${item.name}', '${item.phone}', '${item.company}', '${item.role || ''}')" class="flex-1 ${item.phone ? 'bg-gray-800 hover:bg-gray-900 shadow-md transform hover:-translate-y-0.5' : 'bg-gray-200 text-gray-400 pointer-events-none'} text-white py-4 rounded-xl font-bold flex flex-col items-center justify-center transition-all">
                <span class="text-xl mb-1">💾</span><span class="text-[11px] font-black tracking-wide">저장하기</span>
              </button>
            </div>
          </div>
        </div>
      `;
    }

    function renderEditModal() {
      const d = state.editData;
      const isPast = state.modalType === 'past';
      const isNew = !d.id;

      return `
        <div class="fixed inset-0 bg-gray-50 z-50 flex flex-col">
          <div class="flex justify-between items-center p-4 border-b border-gray-200 bg-white shadow-sm">
            <h2 class="text-xl font-black text-gray-900 tracking-tight">${isNew ? '신규 등록' : '정보 수정'}</h2>
            <button onclick="closeEditModal()" class="text-gray-400 p-2 font-black text-2xl hover:text-red-500 transition">✕</button>
          </div>
          <div class="p-5 flex-1 overflow-y-auto space-y-5 pb-24">
            
            <div class="flex flex-col items-center mb-2">
              <div class="w-32 h-32 bg-white rounded-full flex items-center justify-center text-gray-400 overflow-hidden mb-3 shadow-md border-4 border-white relative cursor-pointer hover:opacity-80 transition group ring-2 ring-gray-100">
                ${d.imgUrl ? `<img src="${d.imgUrl}" class="w-full h-full object-cover"/>` : `<svg class="w-12 h-12" fill="currentColor" viewBox="0 0 20 20"><path fill-rule="evenodd" d="M10 9a3 3 0 100-6 3 3 0 000 6zm-7 9a7 7 0 1114 0H3z" clip-rule="evenodd"></path></svg>`}
                <div class="absolute inset-0 bg-black/50 flex items-center justify-center opacity-0 group-hover:opacity-100 transition-opacity">
                  <span class="text-white text-sm font-bold">사진 변경</span>
                </div>
                <input type="file" accept="image/*" onchange="handleImageUpload(event)" class="absolute inset-0 opacity-0 cursor-pointer" />
              </div>
              <p class="text-[11px] font-bold text-gray-400 text-center">터치하여 사진을 등록/변경하세요<br/>(사진 변경 시 모든 명단에 자동 반영됩니다)</p>
            </div>

            <div class="space-y-4 bg-white p-6 rounded-2xl shadow-sm border border-gray-200">
              ${isPast ? `
                <div><label class="block text-xs font-black text-blue-800 mb-1.5 uppercase">기수(대) <span class="text-red-500">*필수</span></label><input type="number" id="editGen" value="${d.generation || ''}" placeholder="예: 45" class="w-full p-4 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white transition outline-none font-bold text-lg"/></div>
              ` : ''}
              <div><label class="block text-xs font-black text-gray-500 mb-1.5 uppercase">이름 <span class="text-red-500">*필수</span></label><input type="text" id="editName" value="${d.name || ''}" class="w-full p-4 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white transition outline-none font-black text-gray-900 text-lg"/></div>
              <div><label class="block text-xs font-black text-gray-500 mb-1.5 uppercase">연락처 <span class="text-red-500">*필수</span></label><input type="tel" id="editPhone" value="${d.phone || ''}" placeholder="010-0000-0000" class="w-full p-4 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white transition outline-none font-bold text-gray-900"/></div>
              ${!isPast ? `
                <div><label class="block text-xs font-black text-gray-500 mb-1.5 uppercase">직책</label><input type="text" id="editRole" value="${d.role || ''}" placeholder="예: 상임부회장, 총무이사" class="w-full p-4 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white transition outline-none font-bold text-gray-900"/></div>
                <div><label class="block text-xs font-black text-gray-500 mb-1.5 uppercase">입회연도</label><input type="number" id="editJoinYear" value="${d.joinYear || ''}" placeholder="예: 2021" class="w-full p-4 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white transition outline-none font-bold text-gray-900"/></div>
              ` : ''}
              <div><label class="block text-xs font-black text-gray-500 mb-1.5 uppercase">직장명(소속)</label><input type="text" id="editCompany" value="${d.company || ''}" placeholder="직장명 입력" class="w-full p-4 border border-gray-200 rounded-xl bg-gray-50 focus:ring-2 focus:ring-blue-500 focus:bg-white transition outline-none font-bold text-gray-900"/></div>
            </div>
            
            <button onclick="saveEditData()" class="w-full bg-blue-700 text-white font-black text-lg py-5 rounded-2xl shadow-md hover:bg-blue-800 hover:shadow-lg transform hover:-translate-y-0.5 transition-all">저장 및 통합 연동하기</button>
          </div>
        </div>
      `;
    }

    function logout() {
      state.isLoggedIn = false;
      state.userRole = '';
      saveData();
      render();
      showToast('안전하게 로그아웃 되었습니다.');
    }

    function switchTab(tab) {
      state.activeTab = tab;
      state.searchQuery = '';
      render();
    }

    function switchPastTab(tab) {
      state.pastTab = tab;
      state.searchQuery = '';
      render();
    }

    function handleSearch(val) {
      state.searchQuery = val;
    }

    function openMemberModal(id, type) {
      const list = type === 'regular' ? state.regularMembers : state.specialMembers;
      const item = list.find(x => x.id === id);
      if (item) {
        state.selectedItem = { ...item, type };
        state.modalType = 'member';
        render();
      }
    }

    function openPastModal(id, type) {
      const list = type === 'lom' ? state.pastLom : state.pastSpecial;
      const item = list.find(x => x.id === id);
      if (item) {
        state.selectedItem = { ...item, type };
        state.modalType = 'past';
        render();
      }
    }

    function closeModal() {
      state.selectedItem = null;
      render();
    }

    function closeEditModal() {
      state.isEditing = false;
      state.editData = {};
      render();
    }

    function startEditItem() {
      state.editData = { ...state.selectedItem };
      state.selectedItem = null;
      state.isEditing = true;
      render();
    }

    function openAddModal(type) {
      state.modalType = 'member';
      state.editData = { type };
      state.isEditing = true;
      render();
    }

    function openAddPastModal(type) {
      state.modalType = 'past';
      state.editData = { type };
      state.isEditing = true;
      render();
    }

    function handleImageUpload(e) {
      const file = e.target.files[0];
      if (file) {
        const reader = new FileReader();
        reader.onloadend = () => {
          state.editData.imgUrl = reader.result;
          render();
        };
        reader.readAsDataURL(file);
      }
    }

    function saveEditData() {
      const name = document.getElementById('editName').value.trim();
      const phone = document.getElementById('editPhone').value.trim();
      if (!name || !phone) {
        showToast('❌ 이름과 연락처는 필수 입력 항목입니다.');
        return;
      }

      state.editData.name = name;
      state.editData.phone = phone;
      state.editData.company = document.getElementById('editCompany').value.trim();

      let savedId = state.editData.id;

      if (state.modalType === 'member') {
        state.editData.role = document.getElementById('editRole').value.trim();
        state.editData.joinYear = document.getElementById('editJoinYear') ? document.getElementById('editJoinYear').value.trim() : '';
        const list = state.editData.type === 'regular' ? state.regularMembers : state.specialMembers;
        
        if (state.editData.id) {
          const idx = list.findIndex(x => x.id === state.editData.id);
          if (idx !== -1) list[idx] = { ...state.editData };
        } else {
          savedId = 'm_' + Date.now();
          state.editData.id = savedId;
          list.push({ ...state.editData });
        }
      } else {
        const gen = parseInt(document.getElementById('editGen').value);
        if (!gen) {
          showToast('❌ 기수(대)를 숫자로 입력해주세요.');
          return;
        }
        state.editData.generation = gen;
        const list = state.editData.type === 'lom' ? state.pastLom : state.pastSpecial;

        if (state.editData.id && list.findIndex(x => x.id === state.editData.id) !== -1) {
          const idx = list.findIndex(x => x.id === state.editData.id);
          list[idx] = { ...state.editData };
        } else {
          savedId = state.editData.id || ('p_' + Date.now());
          state.editData.id = savedId;
          const existingIdx = list.findIndex(x => x.id === savedId);
          if (existingIdx > -1) list[existingIdx] = { ...state.editData };
          else list.push({ ...state.editData });
        }
      }

      syncMemberInfoGlobally(state.editData);

      saveData();
      state.isEditing = false;
      state.editData = {};
      render();
      showToast('✅ 성공적으로 저장 및 전체 연동되었습니다.');
    }

    render();
  </script>
</body>
</html>
