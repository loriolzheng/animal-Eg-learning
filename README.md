# animal-Eg-learning
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>英语学习网站 - 与小动物一起学英语</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://cdn.jsdelivr.net/npm/font-awesome@4.7.0/css/font-awesome.min.css" rel="stylesheet">
    <script>
        tailwind.config = {
            theme: {
                extend: {
                    colors: {
                        primary: '#4F46E5',
                        secondary: '#EC4899',
                        accent: '#10B981',
                        neutral: '#F3F4F6',
                        'neutral-dark': '#6B7280',
                    },
                    fontFamily: {
                        sans: ['Inter', 'system-ui', 'sans-serif'],
                    },
                    animation: {
                        'bounce-slow': 'bounce 2s infinite',
                        'wiggle': 'wiggle 1s ease-in-out infinite',
                    },
                    keyframes: {
                        wiggle: {
                            '0%, 100%': { transform: 'rotate(-3deg)' },
                            '50%': { transform: 'rotate(3deg)' },
                        }
                    }
                }
            }
        }
    </script>
    <style type="text/tailwindcss">
        @layer utilities {
            .text-shadow {
                text-shadow: 2px 2px 4px rgba(0, 0, 0.2);
            }
            .transition-all-300 {
                transition: all 300ms ease-in-out;
            }
            .animal-card {
                @apply bg-white rounded-2xl shadow-lg p-4 cursor-pointer transform transition-all hover:scale-105 hover:shadow-xl;
            }
            .btn-primary {
                @apply bg-primary text-white px-6 py-3 rounded-lg font-semibold hover:bg-opacity-90 transition-all shadow-md;
            }
            .btn-secondary {
                @apply bg-secondary text-white px-6 py-3 rounded-lg font-semibold hover:bg-opacity-90 transition-all shadow-md;
            }
            .btn-accent {
                @apply bg-accent text-white px-6 py-3 rounded-lg font-semibold hover:bg-opacity-90 transition-all shadow-md;
            }
            .input-primary {
                @apply border-2 border-gray-300 rounded-lg px-4 py-3 focus:outline-none focus:border-primary transition-all;
            }
            .card {
                @apply bg-white rounded-2xl shadow-lg p-6;
            }
        }
    </style>
</head>
<body class="bg-gradient-to-br from-blue-50 to-purple-50 min-h-screen">
    <div id="app" class="container mx-auto px-4 py-8">
        <div id="welcome-screen" class="flex flex-col items-center justify-center min-h-[80vh]">
            <h1 class="text-5xl md:text-6xl font-bold text-center mb-8 text-primary text-shadow">
                与小动物一起学英语
            </h1>
            <p class="text-xl text-center mb-12 max-w-2xl text-neutral-dark">
                选择你喜欢的小动物伙伴，开始你的英语学习之旅吧！
            </p>
            
            <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8 w-full max-w-5xl">
                <div class="animal-card" data-animal="cat">
                    <img src="https://p11-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/1686b166e6c046acbb09e90843dcbddf~tplv-a9rns2rl98-image.image" 
                         alt="猫" class="w-full h-48 object-contain mb-4">
                    <h3 class="text-xl font-bold text-center text-primary">语语</h3>
                </div>
                
                <div class="animal-card" data-animal="dog">
                    <img src="https://p11-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/78e1e263807b4060891ef3c24f4f3955~tplv-a9rns2rl98-image.image" 
                         alt="狗" class="w-full h-48 object-contain mb-4">
                    <h3 class="text-xl font-bold text-center text-primary">旺旺</h3>
                </div>
                
                <div class="animal-card" data-animal="rabbit">
                    <img src="https://p6-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/a62a49f6497848e78ffcaced9c2ea5d6~tplv-a9rns2rl98-image.image" 
                         alt="兔子" class="w-full h-48 object-contain mb-4">
                    <h3 class="text-xl font-bold text-center text-primary">跳跳</h3>
                </div>
                
                <div class="animal-card" data-animal="panda">
                    <img src="https://p26-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/30d09d3445244ef796892a67a4014469~tplv-a9rns2rl98-image.image" 
                         alt="熊猫" class="w-full h-48 object-contain mb-4">
                    <h3 class="text-xl font-bold text-center text-primary">盼盼</h3>
                </div>
            </div>
        </div>

        <div id="learning-screen" class="hidden">
            <div class="flex justify-between items-center mb-8">
                <button id="back-btn" class="flex items-center text-primary font-semibold">
                    <i class="fa fa-arrow-left mr-2"></i> 返回选择
                </button>
                <h2 class="text-2xl font-bold text-primary">英语学习</h2>
                <div class="w-20"></div>
            </div>

            <div class="flex flex-col lg:flex-row gap-8">
                <div class="lg:w-1/3 flex flex-col items-center">
                    <div id="selected-animal" class="w-64 h-64 mb-6 animate-bounce-slow"></div>
                    <div id="animal-speech-bubble" class="bg-white rounded-2xl p-4 shadow-lg mb-6 max-w-xs text-center">
                        你好！我是你的英语学习伙伴。请输入一个单词开始学习吧！
                    </div>
                    <button id="listen-btn" class="btn-primary flex items-center">
                        <i class="fa fa-volume-up mr-2"></i> 听发音
                    </button>
                </div>

                <div class="lg:w-2/3">
                    <div class="card mb-8">
                        <h3 class="text-xl font-bold mb-4 text-primary">单词学习</h3>
                        <div class="flex gap-4 mb-6">
                            <input id="word-input" type="text" class="input-primary flex-grow" placeholder="输入英语或中文单词...">
                            <button id="search-btn" class="btn-primary">
                                <i class="fa fa-search mr-2"></i> 查询
                            </button>
                        </div>
                        <div id="word-result" class="hidden">
                            <div class="flex justify-between items-center mb-4">
                                <h4 id="word-title" class="text-2xl font-bold text-primary"></h4>
                                <button id="play-pronunciation" class="text-accent hover:text-accent/80 transition-all">
                                    <i class="fa fa-volume-up text-2xl"></i>
                                </button>
                            </div>
                            <p id="word-phonetic" class="text-neutral-dark mb-4"></p>
                            <p id="word-chinese" class="text-red-600 font-bold text-lg mb-3"></p>
                            <div id="word-meanings" class="space-y-4"></div>
                        </div>
                    </div>

                    <div class="card mb-8">
                        <h3 class="text-xl font-bold mb-4 text-primary">发音练习</h3>
                        <p class="mb-4 text-neutral-dark">练习朗读单词，获得发音评分</p>
                        <div class="flex gap-4">
                            <button id="start-recording" class="btn-secondary flex items-center">
                                <i class="fa fa-microphone mr-2"></i> 开始录音
                            </button>
                            <button id="stop-recording" class="btn-secondary flex items-center hidden">
                                <i class="fa fa-stop mr-2"></i> 停止录音
                            </button>
                        </div>
                        <div id="recording-status" class="mt-4 hidden">
                            <div class="flex items-center">
                                <div class="w-4 h-4 bg-red-500 rounded-full animate-pulse mr-2"></div>
                                <span>正在录音...</span>
                            </div>
                        </div>
                        <div id="pronunciation-result" class="mt-4 hidden">
                            <h4 class="font-semibold mb-2">发音评分：<span id="pronunciation-score" class="text-accent"></span></h4>
                            <div class="w-full bg-gray-200 rounded-full h-2.5">
                                <div id="score-bar" class="bg-accent h-2.5 rounded-full" style="width: 0%"></div>
                            </div>
                            <p id="pronunciation-feedback" class="mt-2 text-sm"></p>
                        </div>
                    </div>

                    <div class="card">
                        <h3 class="text-xl font-bold mb-4 text-primary">听写练习</h3>
                        <p class="mb-4 text-neutral-dark">选择单词数量，开始听写练习</p>
                        <div class="flex flex-wrap gap-4 mb-6">
                            <button class="dictation-btn px-4 py-2 border-2 border-primary text-primary rounded-lg hover:bg-primary hover:text-white transition-all" data-count="10">10个单词</button>
                            <button class="dictation-btn px-4 py-2 border-2 border-primary text-primary rounded-lg hover:bg-primary hover:text-white transition-all" data-count="15">15个单词</button>
                            <button class="dictation-btn px-4 py-2 border-2 border-primary text-primary rounded-lg hover:bg-primary hover:text-white transition-all" data-count="20">20个单词</button>
                            <button class="dictation-btn px-4 py-2 border-2 border-primary text-primary rounded-lg hover:bg-primary hover:text-white transition-all" data-count="30">30个单词</button>
                        </div>
                        <div id="dictation-area" class="hidden">
                            <div class="flex justify-between items-center mb-4">
                                <h4 class="font-semibold">当前进度：<span id="dictation-progress">0/0</span></h4>
                                <button id="play-dictation-word" class="text-accent hover:text-accent/80 transition-all">
                                    <i class="fa fa-volume-up text-2xl"></i>
                                </button>
                            </div>
                            <input id="dictation-input" type="text" class="input-primary w-full mb-4" placeholder="请输入你听到的单词...">
                            <div class="flex gap-4">
                                <button id="check-dictation" class="btn-accent">检查答案</button>
                                <button id="next-dictation" class="btn-primary hidden">下一个</button>
                            </div>
                            <div id="dictation-result" class="mt-4 hidden">
                                <div id="dictation-correct" class="hidden">
                                    <p class="text-accent font-semibold"><i class="fa fa-check-circle mr-2"></i> 正确！</p>
                                </div>
                                <div id="dictation-wrong" class="hidden">
                                    <p class="text-red-500 font-semibold"><i class="fa fa-times-circle mr-2"></i> 错误</p>
                                    <p>正确答案：<span id="dictation-correct-answer" class="font-semibold"></span></p>
                                </div>
                            </div>
                            <div id="dictation-summary" class="mt-6 hidden">
                                <h4 class="font-bold text-lg mb-2">练习完成！</h4>
                                <p>正确率：<span id="dictation-accuracy" class="font-semibold text-primary"></span></p>
                                <button id="restart-dictation" class="btn-primary mt-4">重新开始</button>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>

    <script>
        const animals = {
            cat: {
                name: "语语",
                image: "https://p11-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/1686b166e6c046acbb09e90843dcbddf~tplv-a9rns2rl98-image.image",
                greetings: ["你好！我是语语，很高兴成为你的英语学习伙伴！","让我们一起学习英语吧！","输入一个单词，开始我们的学习之旅！"]
            },
            dog: {
                name: "旺旺",
                image: "https://p11-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/78e1e263807b4060891ef3c24f4f3955~tplv-a9rns2rl98-image.image",
                greetings: ["汪汪！我是旺旺，你的英语学习伙伴！","准备好学习英语了吗？","输入单词，我们一起学习吧！"]
            },
            rabbit: {
                name: "跳跳",
                image: "https://p6-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/a62a49f6497848e78ffcaced9c2ea5d6~tplv-a9rns2rl98-image.image",
                greetings: ["大家好！我是跳跳，很高兴认识你！","让我们一起快乐学习英语吧！","输入单词开始学习吧！"]
            },
            panda: {
                name: "盼盼",
                image: "https://p26-flow-imagex-sign.byteimg.com/tos-cn-i-a9rns2rl98/rc/pc/super_tool/30d09d3445244ef796892a67a4014469~tplv-a9rns2rl98-image.image",
                greetings: ["你好！我是盼盼，你的英语学习伙伴！","让我们一起学习英语吧！","输入单词，开始学习！"]
            }
        };

        const wordChineseMap = {
            "hello":"你好", "world":"世界", "apple":"苹果", "banana":"香蕉", "computer":"电脑", "phone":"手机",
            "book":"书", "pen":"钢笔", "paper":"纸", "desk":"桌子", "chair":"椅子", "table":"桌子",
            "window":"窗户", "door":"门", "room":"房间", "house":"房子", "car":"汽车", "bus":"公交车",
            "train":"火车", "plane":"飞机", "bird":"鸟", "cat":"猫", "dog":"狗", "fish":"鱼",
            "water":"水", "food":"食物", "milk":"牛奶", "coffee":"咖啡", "tea":"茶", "juice":"果汁",
            "red":"红色", "blue":"蓝色", "green":"绿色", "yellow":"黄色", "black":"黑色", "white":"白色",
            "big":"大的", "small":"小的", "tall":"高的", "short":"短的/矮的", "happy":"开心的",
            "sad":"伤心的", "angry":"生气的", "excited":"兴奋的", "tired":"累的", "hungry":"饿的",
            "thirsty":"渴的", "hot":"热的", "cold":"冷的", "warm":"温暖的", "father":"爸爸",
            "mother":"妈妈", "brother":"兄弟", "sister":"姐妹", "friend":"朋友", "teacher":"老师",
            "student":"学生", "doctor":"医生", "nurse":"护士", "police":"警察",
            "one":"一", "two":"二", "three":"三", "four":"四", "five":"五", "six":"六",
            "seven":"七", "eight":"八", "nine":"九", "ten":"十"
        };

        const englishWords = Object.keys(wordChineseMap);

        let currentState = {
            selectedAnimal: null, currentWord: null, recording: false, recognition: null,
            dictationWords: [], currentDictationIndex: 0, dictationCorrectCount: 0
        };

        const welcomeScreen = document.getElementById('welcome-screen');
        const learningScreen = document.getElementById('learning-screen');
        const animalCards = document.querySelectorAll('.animal-card');
        const backBtn = document.getElementById('back-btn');
        const selectedAnimal = document.getElementById('selected-animal');
        const animalSpeechBubble = document.getElementById('animal-speech-bubble');
        const wordInput = document.getElementById('word-input');
        const searchBtn = document.getElementById('search-btn');
        const wordResult = document.getElementById('word-result');
        const wordTitle = document.getElementById('word-title');
        const wordPhonetic = document.getElementById('word-phonetic');
        const wordChinese = document.getElementById('word-chinese');
        const wordMeanings = document.getElementById('word-meanings');
        const playPronunciation = document.getElementById('play-pronunciation');
        const startRecording = document.getElementById('start-recording');
        const stopRecording = document.getElementById('stop-recording');
        const recordingStatus = document.getElementById('recording-status');
        const pronunciationResult = document.getElementById('pronunciation-result');
        const pronunciationScore = document.getElementById('pronunciation-score');
        const scoreBar = document.getElementById('score-bar');
        const pronunciationFeedback = document.getElementById('pronunciation-feedback');
        const dictationBtns = document.querySelectorAll('.dictation-btn');
        const dictationArea = document.getElementById('dictation-area');
        const dictationProgress = document.getElementById('dictation-progress');
        const playDictationWord = document.getElementById('play-dictation-word');
        const dictationInput = document.getElementById('dictation-input');
        const checkDictation = document.getElementById('check-dictation');
        const nextDictation = document.getElementById('next-dictation');
        const dictationResult = document.getElementById('dictation-result');
        const dictationCorrect = document.getElementById('dictation-correct');
        const dictationWrong = document.getElementById('dictation-wrong');
        const dictationCorrectAnswer = document.getElementById('dictation-correct-answer');
        const dictationSummary = document.getElementById('dictation-summary');
        const dictationAccuracy = document.getElementById('dictation-accuracy');
        const restartDictation = document.getElementById('restart-dictation');
        const listenBtn = document.getElementById('listen-btn');

        function init() {
            animalCards.forEach(card => {
                card.addEventListener('click', () => {
                    const animalType = card.dataset.animal;
                    selectAnimal(animalType);
                });
            });

            backBtn.addEventListener('click', () => { showWelcomeScreen(); });
            searchBtn.addEventListener('click', () => {
                const word = wordInput.value.trim();
                if (word) searchWord(word);
            });
            wordInput.addEventListener('keypress', (e) => {
                if (e.key === 'Enter') {
                    const word = wordInput.value.trim();
                    if (word) searchWord(word);
                }
            });
            playPronunciation.addEventListener('click', () => {
                if (currentState.currentWord) playWordPronunciation(currentState.currentWord);
            });
            startRecording.addEventListener('click', () => {
                if (currentState.currentWord) startPronunciationRecording();
                else showAnimalMessage("请先查询一个单词再进行发音练习！");
            });
            stopRecording.addEventListener('click', () => { stopPronunciationRecording(); });
            dictationBtns.forEach(btn => {
                btn.addEventListener('click', () => {
                    const count = parseInt(btn.dataset.count);
                    startDictation(count);
                });
            });
            playDictationWord.addEventListener('click', () => {
                if (currentState.dictationWords.length > 0 && currentState.currentDictationIndex < currentState.dictationWords.length) {
                    const word = currentState.dictationWords[currentState.currentDictationIndex];
                    speakText(word);
                }
            });
            checkDictation.addEventListener('click', () => { checkDictationAnswer(); });
            nextDictation.addEventListener('click', () => { nextDictationWord(); });
            restartDictation.addEventListener('click', () => {
                const count = currentState.dictationWords.length;
                startDictation(count);
            });
            listenBtn.addEventListener('click', () => {
                if (animalSpeechBubble.textContent) speakText(animalSpeechBubble.textContent);
            });
            initSpeechRecognition();
        }

        function selectAnimal(animalType) {
            currentState.selectedAnimal = animalType;
            const animal = animals[animalType];
            selectedAnimal.innerHTML = `<img src="${animal.image}" alt="${animal.name}" class="w-full h-full object-contain">`;
            const randomGreeting = animal.greetings[Math.floor(Math.random() * animal.greetings.length)];
            showAnimalMessage(randomGreeting);
            showLearningScreen();
        }

        function showWelcomeScreen() {
            welcomeScreen.classList.remove('hidden');
            learningScreen.classList.add('hidden');
            currentState.selectedAnimal = null;
            currentState.currentWord = null;
            resetWordResult();
            resetPronunciationResult();
            resetDictationArea();
        }

        function showLearningScreen() {
            welcomeScreen.classList.add('hidden');
            learningScreen.classList.remove('hidden');
        }

        function showAnimalMessage(message) {
            animalSpeechBubble.textContent = message;
        }

        async function searchWord(word) {
            try {
                const lowerWord = word.toLowerCase();
                const chinese = wordChineseMap[lowerWord] || "暂无中文翻译";
                
                const response = await fetch(`https://api.dictionaryapi.dev/api/v2/entries/en/${encodeURIComponent(word)}`);
                if (!response.ok) throw new Error('Word not found');
                const data = await response.json();
                
                displayWordResult(data[0]);
                currentState.currentWord = data[0];
                wordChinese.textContent = "中文释义：" + chinese;
                
                const animal = animals[currentState.selectedAnimal];
                const messages = [
                    `让我们来学习"${word}"这个单词吧！`,
                    `"${word}"是一个很好的单词，让我们一起学习！`,
                    `你想了解"${word}"的什么呢？发音还是意思？`
                ];
                const randomMessage = messages[Math.floor(Math.random() * messages.length)];
                showAnimalMessage(randomMessage);
                
            } catch (error) {
                console.error('Error searching word:', error);
                showAnimalMessage(`抱歉，我找不到"${word}"这个单词。请尝试其他单词！`);
                resetWordResult();
                currentState.currentWord = null;
            }
        }

        function displayWordResult(wordData) {
            wordTitle.textContent = wordData.word;
            if (wordData.phonetic) {
                wordPhonetic.textContent = wordData.phonetic;
                wordPhonetic.classList.remove('hidden');
            } else {
                wordPhonetic.classList.add('hidden');
            }
            wordMeanings.innerHTML = '';
            wordData.meanings.forEach(meaning => {
                const partOfSpeech = document.createElement('div');
                partOfSpeech.className = 'mb-2';
                partOfSpeech.innerHTML = `<h5 class="font-semibold text-primary">${meaning.partOfSpeech}</h5>`;
                const definitionsList = document.createElement('ul');
                definitionsList.className = 'list-disc pl-5 space-y-1';
                meaning.definitions.forEach(def => {
                    const li = document.createElement('li');
                    li.textContent = def.definition;
                    if (def.example) {
                        const exampleSpan = document.createElement('span');
                        exampleSpan.className = 'text-neutral-dark text-sm block mt-1';
                        exampleSpan.textContent = `例：${def.example}`;
                        li.appendChild(exampleSpan);
                    }
                    definitionsList.appendChild(li);
                });
                partOfSpeech.appendChild(definitionsList);
                wordMeanings.appendChild(partOfSpeech);
            });
            wordResult.classList.remove('hidden');
        }

        function resetWordResult() {
            wordResult.classList.add('hidden');
            wordTitle.textContent = '';
            wordPhonetic.textContent = '';
            wordChinese.textContent = '';
            wordMeanings.innerHTML = '';
        }

        function playWordPronunciation(wordData) {
            if (wordData.phonetics && wordData.phonetics.length > 0) {
                const audioUrl = wordData.phonetics.find(p => p.audio && p.audio.trim() !== '')?.audio;
                if (audioUrl) {
                    const audio = new Audio(audioUrl);
                    audio.play().catch(error => {
                        console.error('Error playing audio:', error);
                        speakText(wordData.word);
                    });
                } else {
                    speakText(wordData.word);
                }
            } else {
                speakText(wordData.word);
            }
        }

        function speakText(text) {
            if ('speechSynthesis' in window) {
                const utterance = new SpeechSynthesisUtterance(text);
                utterance.lang = 'en-US';
                utterance.rate = 0.9;
                utterance.pitch = 1;
                const voices = window.speechSynthesis.getVoices();
                const englishVoice = voices.find(voice => voice.lang.includes('en-US'));
                if (englishVoice) utterance.voice = englishVoice;
                window.speechSynthesis.speak(utterance);
            }
        }

        function initSpeechRecognition() {
            if ('SpeechRecognition' in window || 'webkitSpeechRecognition' in window) {
                const SpeechRecognition = window.SpeechRecognition || window.webkitSpeechRecognition;
                currentState.recognition = new SpeechRecognition();
                currentState.recognition.continuous = false;
                currentState.recognition.interimResults = false;
                currentState.recognition.lang = 'en-US';
                
                currentState.recognition.onresult = (event) => {
                    const transcript = event.results[0][0].transcript.toLowerCase();
                    evaluatePronunciation(transcript);
                };
                currentState.recognition.onerror = (event) => {
                    console.error('Speech recognition error:', event.error);
                    stopPronunciationRecording();
                    showAnimalMessage("语音识别出错了，请重试！");
                };
                currentState.recognition.onend = () => {
                    if (currentState.recording) currentState.recognition.start();
                };
            } else {
                startRecording.disabled = true;
                showAnimalMessage("抱歉，您的浏览器不支持语音识别功能！");
            }
        }

        function startPronunciationRecording() {
            if (!currentState.recognition) {
                showAnimalMessage("抱歉，语音识别功能不可用！");
                return;
            }
            resetPronunciationResult();
            currentState.recording = true;
            startRecording.classList.add('hidden');
            stopRecording.classList.remove('hidden');
            recordingStatus.classList.remove('hidden');
            try { currentState.recognition.start(); } catch (error) { console.error(error); }
        }

        function stopPronunciationRecording() {
            if (!currentState.recognition) return;
            currentState.recording = false;
            startRecording.classList.remove('hidden');
            stopRecording.classList.add('hidden');
            recordingStatus.classList.add('hidden');
            try { currentState.recognition.stop(); } catch (error) { console.error(error); }
        }

        function evaluatePronunciation(transcript) {
            stopPronunciationRecording();
            if (!currentState.currentWord) return;
            const targetWord = currentState.currentWord.word.toLowerCase();
            const userWord = transcript.toLowerCase();
            let score = calculateSimilarity(targetWord, userWord);
            score = Math.max(0, Math.min(100, score));
            pronunciationScore.textContent = `${Math.round(score)}%`;
            scoreBar.style.width = `${score}%`;
            
            if (score >= 80) {
                scoreBar.className = 'bg-accent h-2.5 rounded-full';
                pronunciationFeedback.textContent = "太棒了！发音非常准确！";
                pronunciationFeedback.className = 'mt-2 text-sm text-accent';
            } else if (score >= 60) {
                scoreBar.className = 'bg-yellow-500 h-2.5 rounded-full';
                pronunciationFeedback.textContent = "不错！发音基本准确，继续练习！";
                pronunciationFeedback.className = 'mt-2 text-sm text-yellow-500';
            } else {
                scoreBar.className = 'bg-red-500 h-2.5 rounded-full';
                pronunciationFeedback.textContent = "需要继续练习，尝试更准确地发音！";
                pronunciationFeedback.className = 'mt-2 text-sm text-red-500';
            }
            pronunciationResult.classList.remove('hidden');
        }

        function calculateSimilarity(str1, str2) {
            if (str1 === str2) return 100;
            if (str2.includes(str1)) return 80;
            if (str1.includes(str2)) return 70;
            const distance = levenshteinDistance(str1, str2);
            const maxLength = Math.max(str1.length, str2.length);
            return 100 - (distance / maxLength * 100);
        }

        function levenshteinDistance(str1, str2) {
            const matrix = [];
            for (let i = 0; i <= str2.length; i++) matrix[i] = [i];
            for (let j = 0; j <= str1.length; j++) matrix[0][j] = j;
            for (let i = 1; i <= str2.length; i++) {
                for (let j = 1; j <= str1.length; j++) {
                    if (str2.charAt(i-1) === str1.charAt(j-1)) matrix[i][j] = matrix[i-1][j-1];
                    else matrix[i][j] = Math.min(matrix[i-1][j-1]+1, matrix[i][j-1]+1, matrix[i-1][j]+1);
                }
            }
            return matrix[str2.length][str1.length];
        }

        function resetPronunciationResult() {
            pronunciationResult.classList.add('hidden');
            pronunciationScore.textContent = '';
            scoreBar.style.width = '0%';
            pronunciationFeedback.textContent = '';
        }

        function startDictation(count) {
            currentState.dictationWords = getRandomWords(count);
            currentState.currentDictationIndex = 0;
            currentState.dictationCorrectCount = 0;
            dictationArea.classList.remove('hidden');
            dictationResult.classList.add('hidden');
            dictationSummary.classList.add('hidden');
            updateDictationProgress();
            playCurrentDictationWord();
            dictationInput.value = '';
            showAnimalMessage(`听写练习开始！我们将练习${count}个单词。点击喇叭图标听发音！`);
        }

        function getRandomWords(count) {
            const shuffled = [...englishWords].sort(() => 0.5 - Math.random());
            return shuffled.slice(0, count);
        }

        function updateDictationProgress() {
            dictationProgress.textContent = `${currentState.currentDictationIndex + 1}/${currentState.dictationWords.length}`;
        }

        function playCurrentDictationWord() {
            if (currentState.dictationWords.length > 0 && currentState.currentDictationIndex < currentState.dictationWords.length) {
                const word = currentState.dictationWords[currentState.currentDictationIndex];
                speakText(word);
            }
        }

        function checkDictationAnswer() {
            const userAnswer = dictationInput.value.trim().toLowerCase();
            const correctAnswer = currentState.dictationWords[currentState.currentDictationIndex].toLowerCase();
            dictationResult.classList.remove('hidden');
            checkDictation.classList.add('hidden');
            nextDictation.classList.remove('hidden');
            
            if (userAnswer === correctAnswer) {
                dictationCorrect.classList.remove('hidden');
                dictationWrong.classList.add('hidden');
                currentState.dictationCorrectCount++;
                showAnimalMessage("太棒了！回答正确！");
            } else {
                dictationCorrect.classList.add('hidden');
                dictationWrong.classList.remove('hidden');
                dictationCorrectAnswer.textContent = correctAnswer;
                showAnimalMessage("没关系，继续练习！");
            }
        }

        function nextDictationWord() {
            currentState.currentDictationIndex++;
            dictationResult.classList.add('hidden');
            checkDictation.classList.remove('hidden');
            nextDictation.classList.add('hidden');
            dictationInput.value = '';
            if (currentState.currentDictationIndex >= currentState.dictationWords.length) {
                showDictationSummary();
            } else {
                updateDictationProgress();
                playCurrentDictationWord();
                showAnimalMessage("下一个单词！点击喇叭图标听发音！");
            }
        }

        function showDictationSummary() {
            const accuracy = Math.round((currentState.dictationCorrectCount / currentState.dictationWords.length) * 100);
            dictationAccuracy.textContent = `${accuracy}% (${currentState.dictationCorrectCount}/${currentState.dictationWords.length})`;
            dictationSummary.classList.remove('hidden');
            checkDictation.classList.add('hidden');
            nextDictation.classList.add('hidden');
        }

        function resetDictationArea() {
            dictationArea.classList.add('hidden');
            dictationResult.classList.add('hidden');
            dictationSummary.classList.add('hidden');
            checkDictation.classList.remove('hidden');
            nextDictation.classList.add('hidden');
            dictationInput.value = '';
        }

        document.addEventListener('DOMContentLoaded', init);
    </script>
</body>
</html>
