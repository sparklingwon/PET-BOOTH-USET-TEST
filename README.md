# PET-BOOTH-USET-TEST
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>PET BOOTH 사용자 테스트 참가자 모집</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@400;500;700;900&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Sunset (Vibrant orange, soft peach, deep cocoa brown) -->
    <!-- Application Structure Plan: A dynamic, card-based single-page application. The hero section is more visually striking. Content is organized into distinct, visually separated cards for Intro, Schedule, Benefits, and Details, allowing for non-linear exploration. The schedule is the central interactive element, with a bold calendar and a dynamic time slot display that changes with user clicks. This structure feels more like a modern, engaging app than a static document, prioritizing visual hierarchy and user-driven discovery. -->
    <!-- Visualization & Content Choices: The core interactive visualization is the dynamic calendar/schedule. Report Info: Event dates/times, availability. Goal: Engage, inform, and guide action. Method: A prominent calendar grid with hover effects and a clearly styled selected state. User clicks a date, and a separate section dynamically renders available time slots. Justification: This design moves beyond simple presentation to active user engagement, making the core task (finding a time slot) interactive and fun. All other content is presented in visually distinct, icon-driven cards to maintain high readability and a clean, modern aesthetic. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Noto Sans KR', sans-serif;
            background-color: #FDF4E7;
            color: #5C3D2E;
        }
        .text-primary { color: #5C3D2E; }
        .bg-primary { background-color: #5C3D2E; }
        .bg-card { background-color: #FFFFFF; }
        .accent-bg { background-color: #FF7F50; }
        .accent-text { color: #FF7F50; }
        .hero-bg { background-color: #FFDAB9; }
        .btn-hover:hover { background-color: #FF6347; }
        .date-btn-base { transition: transform 0.2s, background-color 0.2s; }
        .date-btn-base:hover { transform: translateY(-2px); }
        .date-btn-available:hover { background-color: #FFE5CC; }
        .date-btn-selected {
            background-color: #FF7F50 !important;
            color: white !important;
            font-weight: 700;
            transform: scale(1.05);
            box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
        }
        .time-slot-available:hover {
            background-color: #FFDAB9;
            transform: translateY(-2px);
        }
        .form-input {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 8px;
            font-size: 1rem;
            color: #5C3D2E;
            margin-bottom: 1rem;
        }
    </style>
</head>
<body>
    <div class="container mx-auto p-4 md:p-8 max-w-5xl">
        <header class="text-center py-20 md:py-24 hero-bg rounded-3xl shadow-2xl p-8 mb-16 relative overflow-hidden">
            <h1 class="text-5xl md:text-6xl font-black mb-4 leading-tight">
                <span class="accent-text">세상에서 가장 특별한 순간,</span><br>우리 아이 발자국을 남겨보세요!
            </h1>
            <p class="text-lg md:text-xl text-primary mt-4 mb-8 max-w-2xl mx-auto">
                국내 최초 반려동물 전용 셀프 포토부스, 🐾PET BOOTH 사용자 테스트에 소중한 반려동물과 함께할 첫 번째 참가자를 모집합니다.
            </p>
            <a href="#schedule" class="accent-bg text-white font-bold py-4 px-10 rounded-full text-lg md:text-xl btn-hover transition-all duration-300 shadow-md">
                지금 바로 신청하기
            </a>
            <div class="absolute bottom-0 right-0 opacity-10 text-[10rem] md:text-[15rem] leading-[0]">🐾</div>
        </header>

        <main class="space-y-16">
            <section id="intro" class="bg-card p-8 rounded-3xl shadow-lg">
                <h2 class="text-3xl font-bold text-center mb-10 text-primary">✨ PET BOOTH, 어떤 경험인가요?</h2>
                <div class="grid md:grid-cols-2 gap-10 text-center">
                    <div class="p-6 rounded-2xl border-2 border-dashed border-gray-200">
                        <div class="text-5xl mb-4 accent-text">🐾</div>
                        <h3 class="text-2xl font-bold mb-2 text-primary">젤리샷 (발바닥샷)</h3>
                        <p class="text-gray-600">세상에 단 하나뿐인 우리 아이의 사랑스러운 발바닥을 선명하게 기록하는 특별한 순간</p>
                    </div>
                    <div class="p-6 rounded-2xl border-2 border-dashed border-gray-200">
                        <div class="text-5xl mb-4 accent-text">📸</div>
                        <h3 class="text-2xl font-bold mb-2 text-primary">탤런트샷 (정면샷)</h3>
                        <p class="text-gray-600">정면을 바라보는 가장 예쁜 모습을 포착하여 우리 아이만의 매력을 가득 담아내는 시간</p>
                    </div>
                </div>
            </section>

            <section id="schedule" class="bg-card p-8 rounded-3xl shadow-lg">
                <h2 class="text-3xl font-bold text-center mb-4 text-primary">🗓️ 원하시는 날짜와 시간을 선택하세요</h2>
                <p class="text-center text-gray-600 mb-8">테스트는 9월 15일부터 26일까지 진행됩니다. 가능한 날짜를 선택하여 시간을 확인해보세요. (총 20팀 선착순 마감)</p>
                <div id="calendar-grid" class="grid grid-cols-5 gap-3 mb-8">
                </div>
                <div id="time-slots-container" class="text-center p-6 bg-gray-50 rounded-2xl border border-dashed border-gray-300">
                    <p class="text-gray-600 font-semibold">날짜를 선택하면 예약 가능한 시간이 표시됩니다.</p>
                </div>
                 <!-- Application form container (initially hidden) -->
                <div id="application-form-container" class="hidden text-left p-6 bg-gray-50 rounded-2xl border border-dashed border-gray-300 mt-8">
                    <h3 class="text-xl font-bold mb-4 text-primary text-center">참가 신청 정보 입력</h3>
                    <p class="text-center text-gray-600 mb-4">선택하신 날짜와 시간: <span id="selected-datetime" class="font-bold accent-text"></span></p>
                    <form id="application-form" class="space-y-4">
                        <!-- Guardian Info -->
                        <div class="flex flex-col">
                            <label for="guardian-name" class="font-semibold text-primary mb-1">보호자 성함</label>
                            <input type="text" id="guardian-name" name="guardianName" class="form-input" placeholder="성함을 입력해주세요" required>
                        </div>
                        <div class="flex flex-col">
                            <label for="guardian-contact" class="font-semibold text-primary mb-1">보호자 연락처</label>
                            <input type="tel" id="guardian-contact" name="guardianContact" class="form-input" placeholder="연락처를 입력해주세요 (예: 010-1234-5678)" required>
                        </div>

                        <!-- Pet Info -->
                        <div class="flex flex-col">
                            <label for="pet-name" class="font-semibold text-primary mb-1">반려동물 이름</label>
                            <input type="text" id="pet-name" name="petName" class="form-input" placeholder="이름을 입력해주세요" required>
                        </div>
                        <div class="flex flex-col">
                            <label for="pet-age" class="font-semibold text-primary mb-1">반려동물 나이</label>
                            <input type="text" id="pet-age" name="petAge" class="form-input" placeholder="나이를 입력해주세요 (예: 3살)" required>
                        </div>
                        <div class="flex flex-col">
                            <label for="pet-breed" class="font-semibold text-primary mb-1">반려동물 품종</label>
                            <input type="text" id="pet-breed" name="petBreed" class="form-input" placeholder="품종을 입력해주세요 (예: 푸들, 코숏)" required>
                        </div>
                        <div class="flex flex-col">
                            <label class="font-semibold text-primary mb-1">반려동물 성별</label>
                            <div class="flex items-center space-x-4">
                                <label class="flex items-center">
                                    <input type="radio" name="petGender" value="수컷" class="form-radio" required>
                                    <span class="ml-2 text-primary">수컷</span>
                                </label>
                                <label class="flex items-center">
                                    <input type="radio" name="petGender" value="암컷" class="form-radio" required>
                                    <span class="ml-2 text-primary">암컷</span>
                                </label>
                                <label class="flex items-center">
                                    <input type="radio" name="petGender" value="중성화" class="form-radio" required>
                                    <span class="ml-2 text-primary">중성화</span>
                                </label>
                            </div>
                        </div>

                        <button type="submit" class="w-full accent-bg text-white font-bold py-3 px-6 rounded-full text-lg btn-hover transition-all duration-300 shadow-lg mt-6">
                            참가 신청 완료하기
                        </button>
                    </form>
                </div>
            </section>

            <section id="benefits" class="bg-card p-8 rounded-3xl shadow-lg">
                <h2 class="text-3xl font-bold text-center mb-10 text-primary">🎁 참가자 전원에게 드리는 특별한 혜택</h2>
                <div class="grid md:grid-cols-3 gap-8 text-center">
                    <div class="p-4">
                        <div class="text-5xl mb-3">📷</div>
                        <h3 class="text-xl font-bold mb-2 text-primary">무료 촬영 체험</h3>
                        <p class="text-gray-600">젤리샷과 탤런트샷, 두 가지 컨셉의 촬영을 모두 무료로 경험할 수 있습니다.</p>
                    </div>
                    <div class="p-4">
                        <div class="text-5xl mb-3">🖼️</div>
                        <h3 class="text-xl font-bold mb-2 text-primary">즉석 사진 출력</h3>
                        <p class="text-gray-600">촬영 후 가장 마음에 드는 사진을 바로 인화하여 소중한 추억을 간직하세요.</p>
                    </div>
                    <div class="p-4">
                        <div class="text-5xl mb-3">💝</div>
                        <h3 class="text-xl font-bold mb-2 text-primary">한정 기념품 증정</h3>
                        <p class="text-gray-600">PET BOOTH 테스트 참여자만을 위해 특별히 제작된 기념품을 선물로 드립니다.</p>
                    </div>
                </div>
            </section>

            <section id="details" class="grid md:grid-cols-2 gap-8">
                <div class="bg-card p-8 rounded-3xl shadow-lg">
                    <h2 class="text-2xl font-bold mb-4 text-primary">📍 오시는 길</h2>
                    <p class="font-semibold text-lg text-primary">퍼뮤니티 본사 R&D CENTER</p>
                    <p class="text-gray-600 mb-4">서울 성동구 상원12길 34, 서울숲에이원센터 8층 808호</p>
                    <a href="https://map.kakao.com/link/to/퍼뮤니티,37.5482,127.0450" target="_blank" class="inline-block accent-bg text-white font-bold py-2 px-4 rounded-full text-sm hover:bg-orange-600 transition-all duration-300">
                        카카오맵으로 길찾기
                    </a>
                </div>
                <div class="bg-card p-8 rounded-3xl shadow-lg">
                    <h2 class="text-2xl font-bold mb-4 text-primary">🙋 참여 대상</h2>
                    <p class="font-semibold text-lg text-primary">보호자를 동반한 반려견·반려묘</p>
                    <p class="text-gray-600">기본 건강 상태가 양호하고 사회성이 보통 이상인 사랑스러운 친구들을 기다립니다.</p>
                </div>
            </section>
            
            <section id="notice" class="bg-card p-8 rounded-3xl shadow-lg">
                <h2 class="text-3xl font-bold text-center mb-8 text-primary">⚠️ 꼭 확인해주세요!</h2>
                <ul class="space-y-4 max-w-2xl mx-auto text-gray-600">
                    <li class="flex items-start"><span class="accent-text text-xl font-bold mr-3">✓</span><div>촬영 전 참가자 스크리닝 및 동의서 작성이 필요합니다.</div></li>
                    <li class="flex items-start"><span class="accent-text text-xl font-bold mr-3">✓</span><div>반려동물의 안전과 위생을 위해 세션 간 청소·살균 시간이 포함됩니다.</div></li>
                    <li class="flex items-start"><span class="accent-text text-xl font-bold mr-3">✓</span><div>공격성, 전염성 질환, 최근 수술 이력이 있는 반려동물은 참여가 제한될 수 있습니다.</div></li>
                    <li class="flex items-start"><span class="accent-text text-xl font-bold mr-3">✓</span><div>마케팅 활용 동의는 선택 사항이며, 동의하지 않으셔도 테스트 참여에 불이익은 없습니다.</div></li>
                </ul>
            </section>

            <!-- Brand Story Footer -->
            <footer id="brand-story" class="text-center py-12 hero-bg rounded-3xl shadow-inner">
                <h2 class="text-4xl font-black mb-4 text-primary">
                    
                </h2>
                <h2 class="text-4xl font-black mb-4 text-primary">
                    반려동물과 함께 만드는, 더 나은 내일
                </h2>
                <p class="text-lg text-gray-600 mb-8">퍼뮤니티는 사랑스러운 반려동물과의 동행을 더 가치있게 만듭니다.</p>
                <a href="https://furmunity.github.io/petbooth/" class="accent-bg text-white font-bold py-4 px-12 rounded-full text-xl btn-hover transition-all duration-300 shadow-lg" target="_blank">
                    브랜드 비전 자세히 보기
                </a>
            </footer>
        </main>
    </div>

    <script>
        document.addEventListener('DOMContentLoaded', () => {
            const scheduleData = {
                '2025-09-15': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-16': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-17': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-18': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-19': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-22': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-23': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-24': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-25': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
                '2025-09-26': { '09:30': 'available', '11:00': 'available', '14:00': 'available', '15:30': 'available' },
            };

            const calendarGrid = document.getElementById('calendar-grid');
            const timeSlotsContainer = document.getElementById('time-slots-container');
            const applicationFormContainer = document.getElementById('application-form-container');
            const applicationForm = document.getElementById('application-form');
            const selectedDatetimeDisplay = document.getElementById('selected-datetime');

            let selectedDateBtn = null;
            let selectedTimeSlot = null;
            const weekDays = ['일', '월', '화', '수', '목', '금', '토'];

            // Iterate over the keys (dates) in the scheduleData object
            Object.keys(scheduleData).forEach(dateISO => {
                const d = new Date(dateISO + 'T00:00:00');
                const day = d.getDate();
                const weekDay = weekDays[d.getDay()];

                // Determine if any time slot is available for this date
                const isAvailable = Object.values(scheduleData[dateISO]).some(status => status === 'available');

                const dateBtn = document.createElement('button');
                dateBtn.classList.add('p-3', 'rounded-xl', 'date-btn-base', 'text-primary', 'font-semibold', 'flex', 'flex-col', 'items-center', 'justify-center', 'shadow-md');
                dateBtn.innerHTML = `
                    <span class="text-xl md:text-2xl font-black">${day}</span>
                    <span class="text-sm md:text-base">${weekDay}</span>
                `;
                dateBtn.dataset.date = dateISO;
                dateBtn.disabled = !isAvailable;

                if (isAvailable) {
                    dateBtn.classList.add('bg-card', 'date-btn-available');
                } else {
                    dateBtn.classList.add('bg-gray-200', 'text-gray-400', 'cursor-not-allowed');
                }

                dateBtn.addEventListener('click', () => {
                    if (selectedDateBtn) {
                        selectedDateBtn.classList.remove('date-btn-selected');
                    }
                    dateBtn.classList.add('date-btn-selected');
                    selectedDateBtn = dateBtn;
                    // Reset time slot selection and hide form
                    if (selectedTimeSlot) {
                        selectedTimeSlot.classList.remove('date-btn-selected');
                        selectedTimeSlot = null;
                    }
                    applicationFormContainer.classList.add('hidden');
                    timeSlotsContainer.classList.remove('hidden');
                    renderTimeSlots(dateISO);
                });
                calendarGrid.appendChild(dateBtn);
            });
            
            function renderTimeSlots(date) {
                const slots = scheduleData[date];
                timeSlotsContainer.innerHTML = '';
                
                const header = document.createElement('h3');
                header.className = 'text-xl font-bold mb-4 text-primary';
                header.textContent = `${new Date(date).toLocaleDateString('ko-KR', { month: 'long', day: 'numeric', weekday: 'long' })} 예약 현황`;
                timeSlotsContainer.appendChild(header);

                const slotsGrid = document.createElement('div');
                slotsGrid.className = 'grid grid-cols-2 md:grid-cols-4 gap-4';

                if (slots) {
                    Object.entries(slots).forEach(([time, status]) => {
                        const slotEl = document.createElement('div');
                        const isAvailable = status === 'available';
                        slotEl.classList.add('p-4', 'rounded-xl', 'text-center', 'font-semibold', 'text-primary', 'date-btn-base');
                        if (isAvailable) {
                            slotEl.classList.add('bg-white', 'shadow-md', 'cursor-pointer', 'time-slot-available');
                            slotEl.addEventListener('click', () => {
                                if (selectedTimeSlot) {
                                    selectedTimeSlot.classList.remove('date-btn-selected');
                                }
                                slotEl.classList.add('date-btn-selected');
                                selectedTimeSlot = slotEl;
                                timeSlotsContainer.classList.add('hidden');
                                applicationFormContainer.classList.remove('hidden');
                                selectedDatetimeDisplay.textContent = `${new Date(date).toLocaleDateString('ko-KR')} ${time}`;
                                document.getElementById('application-form').scrollIntoView({ behavior: 'smooth' });
                            });
                        } else {
                            slotEl.classList.add('bg-gray-200', 'text-gray-500', 'cursor-not-allowed');
                        }

                        slotEl.innerHTML = `
                            <p class="text-xl">${time}</p>
                            <p class="text-sm">${isAvailable ? '예약 가능' : '마감'}</p>
                        `;
                        slotsGrid.appendChild(slotEl);
                    });
                }
                
                timeSlotsContainer.appendChild(slotsGrid);
            }

            applicationForm.addEventListener('submit', (e) => {
                e.preventDefault();
                
                const formData = new FormData(applicationForm);
                const data = Object.fromEntries(formData.entries());

                const confirmationMessage = `
                    참가 신청이 완료되었습니다. 감사합니다!
                    \n\n[신청 정보]
                    날짜/시간: ${selectedDatetimeDisplay.textContent}
                    보호자 성함: ${data.guardianName}
                    보호자 연락처: ${data.guardianContact}
                    반려동물 이름: ${data.petName}
                    반려동물 나이: ${data.petAge}
                    반려동물 품종: ${data.petBreed}
                    반려동물 성별: ${data.petGender}
                `;
                
                // Use a simple modal or message box instead of alert()
                const messageBox = document.createElement('div');
                messageBox.innerHTML = `
                    <div style="position:fixed;top:0;left:0;width:100%;height:100%;background:rgba(0,0,0,0.5);display:flex;justify-content:center;align-items:center;z-index:100;">
                        <div style="background:#fff;padding:2rem;border-radius:1rem;max-width:90%;text-align:center;box-shadow:0 10px 25px rgba(0,0,0,0.2);">
                            <h3 style="font-size:1.5rem;font-weight:bold;margin-bottom:1rem;color:#5C3D2E;">신청 완료!</h3>
                            <p style="white-space:pre-wrap;text-align:left;line-height:1.6;font-size:1rem;color:#555;">${confirmationMessage}</p>
                            <button onclick="this.parentNode.parentNode.remove()" style="margin-top:1.5rem;padding:0.75rem 2rem;background:#FF7F50;color:white;border-radius:9999px;font-weight:bold;">확인</button>
                        </div>
                    </div>
                `;
                document.body.appendChild(messageBox);
                
                applicationForm.reset();
                selectedDateBtn.classList.remove('date-btn-selected');
                selectedTimeSlot.classList.remove('date-btn-selected');
                selectedDateBtn = null;
                selectedTimeSlot = null;
                applicationFormContainer.classList.add('hidden');
                timeSlotsContainer.classList.remove('hidden');

            });
            
            document.querySelectorAll('a[href^="#"]').forEach(anchor => {
                anchor.addEventListener('click', function (e) {
                    e.preventDefault();
                    document.querySelector(this.getAttribute('href')).scrollIntoView({
                        behavior: 'smooth'
                    });
                });
            });
        });
    </script>
</body>
</html>
