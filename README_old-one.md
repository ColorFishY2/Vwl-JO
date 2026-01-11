
<!DOCTYPE html>
<html lang="de">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Fragebogen - Freie Marktwirtschaft</title>
    <style>
        :root {
            --color-bg-primary: #f5f5f5;
            --color-text: #1a1a1a;
            --color-primary: #2a8a6e;
            --color-success: #28a745;
            --color-error: #dc3545;
            --color-warning: #ffc107;
            --color-white: #ffffff;
            --color-light-gray: #f8f9fa;
            --color-border: #dee2e6;
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
            background-color: var(--color-bg-primary);
            color: var(--color-text);
            line-height: 1.6;
            padding: 20px;
        }

        .container {
            max-width: 900px;
            margin: 0 auto;
            background: var(--color-white);
            border-radius: 12px;
            box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
            overflow: hidden;
        }

        .header {
            background: linear-gradient(135deg, #2a8a6e 0%, #1f6854 100%);
            color: var(--color-white);
            padding: 40px 20px;
            text-align: center;
        }

        .header h1 {
            font-size: 28px;
            margin-bottom: 10px;
        }

        .header p {
            font-size: 14px;
            opacity: 0.9;
        }

        .content {
            padding: 30px 20px;
        }

        .section {
            margin-bottom: 40px;
        }

        .section-title {
            font-size: 20px;
            font-weight: 600;
            color: var(--color-primary);
            margin-bottom: 20px;
            padding-bottom: 10px;
            border-bottom: 2px solid var(--color-primary);
        }

        .question-block {
            margin: 25px 0;
            padding: 15px;
            background: var(--color-light-gray);
            border-radius: 8px;
            border-left: 4px solid var(--color-border);
            transition: all 0.3s ease;
        }

        .question-block.correct {
            background: #d4edda;
            border-left-color: var(--color-success);
        }

        .question-block.incorrect {
            background: #f8d7da;
            border-left-color: var(--color-error);
        }

        .question-label {
            font-weight: 600;
            font-size: 16px;
            margin-bottom: 12px;
            color: var(--color-text);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .question-type-badge {
            display: inline-block;
            font-size: 11px;
            padding: 3px 8px;
            background: var(--color-primary);
            color: white;
            border-radius: 4px;
            margin-left: auto;
            white-space: nowrap;
        }

        .type-freetext {
            background: #9c27b0;
        }

        .type-multiple {
            background: #2196f3;
        }

        .options {
            display: flex;
            flex-direction: column;
            gap: 8px;
        }

        .option {
            padding: 10px 12px;
            background: var(--color-white);
            border: 2px solid var(--color-border);
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.3s ease;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .option:hover {
            border-color: var(--color-primary);
            background: #f0f8f6;
        }

        .option input[type="radio"] {
            cursor: pointer;
            margin: 0;
        }

        .option label {
            cursor: pointer;
            flex: 1;
            margin: 0;
        }

        .freetext-input {
            width: 100%;
            padding: 10px 12px;
            border: 2px solid var(--color-border);
            border-radius: 6px;
            font-family: inherit;
            font-size: 14px;
            margin-top: 10px;
            transition: border-color 0.3s ease;
        }

        .freetext-input:focus {
            outline: none;
            border-color: var(--color-primary);
        }

        .feedback {
            margin-top: 10px;
            padding: 10px 12px;
            border-radius: 6px;
            display: none;
            font-weight: 500;
        }

        .feedback.show {
            display: block;
        }

        .feedback.correct {
            background: #c3e6cb;
            color: #155724;
            border-left: 3px solid var(--color-success);
        }

        .feedback.incorrect {
            background: #f5c6cb;
            color: #721c24;
            border-left: 3px solid var(--color-error);
        }

        .check-button {
            margin-top: 10px;
            padding: 10px 16px;
            background: var(--color-primary);
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            transition: background 0.3s ease;
        }

        .check-button:hover {
            background: #1f6854;
        }

        .check-button:disabled {
            background: #ccc;
            cursor: not-allowed;
        }

        .progress-bar {
            width: 100%;
            height: 8px;
            background: var(--color-border);
            border-radius: 4px;
            margin: 15px 0;
            overflow: hidden;
        }

        .progress-fill {
            height: 100%;
            background: var(--color-success);
            transition: width 0.3s ease;
        }

        .progress-text {
            text-align: center;
            font-weight: 600;
            color: var(--color-text);
            margin-bottom: 20px;
        }

        .footer {
            padding: 20px;
            background: var(--color-light-gray);
            text-align: center;
            border-top: 1px solid var(--color-border);
        }

        .download-btn {
            padding: 12px 24px;
            background: var(--color-success);
            color: white;
            border: none;
            border-radius: 6px;
            cursor: pointer;
            font-weight: 600;
            font-size: 14px;
            transition: background 0.3s ease;
        }

        .download-btn:hover {
            background: #218838;
        }

        .download-btn:disabled {
            background: #ccc;
            cursor: not-allowed;
        }

        .icon-correct::before {
            content: "✓ ";
            color: var(--color-success);
            font-weight: bold;
        }

        .icon-incorrect::before {
            content: "✗ ";
            color: var(--color-error);
            font-weight: bold;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="header">
            <h1>Fragebogen - Freie Marktwirtschaft</h1>
            <p>Teste dein Wissen! 6 Fragen zum Ausfüllen, 5 Fragen Multiple-Choice</p>
        </div>

        <div class="content">
            <div class="progress-text">
                <span id="answered">0</span>/<span id="total">11</span> beantwortet
            </div>
            <div class="progress-bar">
                <div class="progress-fill" id="progress"></div>
            </div>

            <!-- Sektion 1 -->
            <div class="section">
                <h2 class="section-title">1️⃣ Grundkonzepte der freien Marktwirtschaft</h2>

                <!-- Frage 1: Freier Text -->
                <div class="question-block" id="q1-block">
                    <div class="question-label">
                        1. Was ist der Preismechanismus?
                        <span class="question-type-badge type-freetext">Freitext</span>
                    </div>
                    <input type="text" class="freetext-input" id="q1" placeholder="Deine Antwort..." onkeyup="delayCheck(1, ['Preismechanismus', 'lenkt', 'Ressourcen', 'Preissignale'])">
                    <div class="feedback" id="q1-feedback"></div>
                </div>

                <!-- Frage 2: Freier Text -->
                <div class="question-block" id="q2-block">
                    <div class="question-label">
                        2. Was ist eine wichtige Voraussetzung für freie Marktwirtschaft?
                        <span class="question-type-badge type-freetext">Freitext</span>
                    </div>
                    <input type="text" class="freetext-input" id="q2" placeholder="Deine Antwort..." onkeyup="delayCheck(2, ['Privateigentum', 'Eigentum'])">
                    <div class="feedback" id="q2-feedback"></div>
                </div>
            </div>

            <!-- Sektion 2 -->
            <div class="section">
                <h2 class="section-title">2️⃣ Vorteile der freien Marktwirtschaft</h2>

                <!-- Frage 3: Multiple Choice -->
                <div class="question-block" id="q3-block">
                    <div class="question-label">
                        3. Welcher Vorteil entsteht durch Wettbewerb zwischen Unternehmen?
                        <span class="question-type-badge type-multiple">Auswahl</span>
                    </div>
                    <div class="options">
                        <label class="option">
                            <input type="radio" name="q3" value="Innovation und Effizienz">
                            <span>Innovation und Effizienz</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q3" value="Höhere Preise">
                            <span>Höhere Preise</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q3" value="Weniger Auswahl">
                            <span>Weniger Auswahl</span>
                        </label>
                    </div>
                    <div class="feedback" id="q3-feedback"></div>
                </div>

                <!-- Frage 4: Freier Text -->
                <div class="question-block" id="q4-block">
                    <div class="question-label">
                        4. Was ist die „unsichtbare Hand" von Adam Smith?
                        <span class="question-type-badge type-freetext">Freitext</span>
                    </div>
                    <input type="text" class="freetext-input" id="q4" placeholder="Deine Antwort..." onkeyup="delayCheck(4, ['egoistisch', 'Handlungen', 'Gemeinwohl', 'Smith'])">
                    <div class="feedback" id="q4-feedback"></div>
                </div>

                <!-- Frage 5: Multiple Choice -->
                <div class="question-block" id="q5-block">
                    <div class="question-label">
                        5. Warum streben Unternehmen nach Gewinn?
                        <span class="question-type-badge type-multiple">Auswahl</span>
                    </div>
                    <div class="options">
                        <label class="option">
                            <input type="radio" name="q5" value="Aus Tradition">
                            <span>Aus Tradition</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q5" value="Staat verbietet Verlust">
                            <span>Staat verbietet Verlust</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q5" value="Investitionen finanzieren und Risiken abdecken">
                            <span>Investitionen finanzieren und Risiken abdecken</span>
                        </label>
                    </div>
                    <div class="feedback" id="q5-feedback"></div>
                </div>
            </div>

            <!-- Sektion 3 -->
            <div class="section">
                <h2 class="section-title">3️⃣ Nachteile und Marktversagen</h2>

                <!-- Frage 6: Multiple Choice -->
                <div class="question-block" id="q6-block">
                    <div class="question-label">
                        6. Was ist ein Monopol?
                        <span class="question-type-badge type-multiple">Auswahl</span>
                    </div>
                    <div class="options">
                        <label class="option">
                            <input type="radio" name="q6" value="Vollständiger Wettbewerb">
                            <span>Vollständiger Wettbewerb</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q6" value="Ein Anbieter kontrolliert den Markt">
                            <span>Ein Anbieter kontrolliert den Markt</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q6" value="Viele kleine Anbieter">
                            <span>Viele kleine Anbieter</span>
                        </label>
                    </div>
                    <div class="feedback" id="q6-feedback"></div>
                </div>

                <!-- Frage 7: Freier Text -->
                <div class="question-block" id="q7-block">
                    <div class="question-label">
                        7. Welches Problem entsteht durch externe Effekte?
                        <span class="question-type-badge type-freetext">Freitext</span>
                    </div>
                    <input type="text" class="freetext-input" id="q7" placeholder="Deine Antwort..." onkeyup="delayCheck(7, ['externe', 'Kosten', 'Nutzen', 'Markt', 'erfasst'])">
                    <div class="feedback" id="q7-feedback"></div>
                </div>

                <!-- Frage 8: Multiple Choice -->
                <div class="question-block" id="q8-block">
                    <div class="question-label">
                        8. Wann muss der Staat eingreifen?
                        <span class="question-type-badge type-multiple">Auswahl</span>
                    </div>
                    <div class="options">
                        <label class="option">
                            <input type="radio" name="q8" value="Immer, um alle Probleme zu lösen">
                            <span>Immer, um alle Probleme zu lösen</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q8" value="Bei Marktversagen und zum Schutz von Bürgern">
                            <span>Bei Marktversagen und zum Schutz von Bürgern</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q8" value="Nie, der Markt regelt sich selbst">
                            <span>Nie, der Markt regelt sich selbst</span>
                        </label>
                    </div>
                    <div class="feedback" id="q8-feedback"></div>
                </div>
            </div>

            <!-- Sektion 4 -->
            <div class="section">
                <h2 class="section-title">4️⃣ Praktische Anwendung und Kritisches Denken</h2>

                <!-- Frage 9: Freier Text -->
                <div class="question-block" id="q9-block">
                    <div class="question-label">
                        9. Ist Deutschland eine reine freie Marktwirtschaft?
                        <span class="question-type-badge type-freetext">Freitext</span>
                    </div>
                    <input type="text" class="freetext-input" id="q9" placeholder="Deine Antwort..." onkeyup="delayCheck(9, ['Nein', 'soziale', 'Marktwirtschaft', 'Deutschland'])">
                    <div class="feedback" id="q9-feedback"></div>
                </div>

                <!-- Frage 10: Freier Text -->
                <div class="question-block" id="q10-block">
                    <div class="question-label">
                        10. Nenne einen Unterschied zwischen Marktwirtschaft und Planwirtschaft.
                        <span class="question-type-badge type-freetext">Freitext</span>
                    </div>
                    <input type="text" class="freetext-input" id="q10" placeholder="Deine Antwort..." onkeyup="delayCheck(10, ['Preis', 'Planung', 'Markt', 'zentral', 'Unterschied'])">
                    <div class="feedback" id="q10-feedback"></div>
                </div>

                <!-- Frage 11: Multiple Choice -->
                <div class="question-block" id="q11-block">
                    <div class="question-label">
                        11. Was sind positive Aspekte der freien Marktwirtschaft?
                        <span class="question-type-badge type-multiple">Auswahl</span>
                    </div>
                    <div class="options">
                        <label class="option">
                            <input type="radio" name="q11" value="Effizienz, Innovation, Wahlfreiheit">
                            <span>Effizienz, Innovation, Wahlfreiheit</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q11" value="Zentraler Plan löst alles">
                            <span>Zentraler Plan löst alles</span>
                        </label>
                        <label class="option">
                            <input type="radio" name="q11" value="Keine Probleme jemals">
                            <span>Keine Probleme jemals</span>
                        </label>
                    </div>
                    <div class="feedback" id="q11-feedback"></div>
                </div>
            </div>
        </div>

        <div class="footer">
            <button class="download-btn" id="downloadBtn" onclick="downloadHTML()">📥 Als HTML herunterladen</button>
        </div>
    </div>

    <script>
        const answered = new Set();
        let timeoutId = {};

        function checkFreetext(questionNum, keywordList) {
            const input = document.getElementById(`q${questionNum}`);
            const feedback = document.getElementById(`q${questionNum}-feedback`);
            const block = document.getElementById(`q${questionNum}-block`);
            const answer = input.value.trim().toLowerCase();

            if (!answer) {
                feedback.className = 'feedback';
                block.classList.remove('correct', 'incorrect');
                if (answered.has(questionNum)) {
                    answered.delete(questionNum);
                    updateProgress();
                }
                return;
            }

            // Überprüfe ob mindestens ein Schlüsselwort enthalten ist
            const isCorrect = keywordList.some(keyword => 
                answer.includes(keyword.toLowerCase())
            );

            if (isCorrect) {
                feedback.className = 'feedback show correct icon-correct';
                feedback.textContent = '✓ Korrekt!';
                block.classList.add('correct');
                block.classList.remove('incorrect');
            } else {
                feedback.className = 'feedback show incorrect icon-incorrect';
                feedback.textContent = `✗ Nicht ganz richtig. Suchbegriffe: ${keywordList.join(', ')}`;
                block.classList.add('incorrect');
                block.classList.remove('correct');
            }

            if (!answered.has(questionNum)) {
                answered.add(questionNum);
                updateProgress();
            }
        }

        function delayCheck(questionNum, keywordList) {
            clearTimeout(timeoutId[questionNum]);
            timeoutId[questionNum] = setTimeout(() => {
                checkFreetext(questionNum, keywordList);
            }, 3000);
        }

        function checkMultiple(questionNum, correctAnswer) {
            const selected = document.querySelector(`input[name="q${questionNum}"]:checked`);
            const feedback = document.getElementById(`q${questionNum}-feedback`);
            const block = document.getElementById(`q${questionNum}-block`);

            if (!selected) {
                feedback.className = 'feedback';
                block.classList.remove('correct', 'incorrect');
                if (answered.has(questionNum)) {
                    answered.delete(questionNum);
                    updateProgress();
                }
                return;
            }

            const isCorrect = selected.value === correctAnswer;

            if (isCorrect) {
                feedback.className = 'feedback show correct icon-correct';
                feedback.textContent = '✓ Korrekt!';
                block.classList.add('correct');
                block.classList.remove('incorrect');
            } else {
                feedback.className = 'feedback show incorrect icon-incorrect';
                feedback.textContent = `✗ Falsch! Richtige Antwort: ${correctAnswer}`;
                block.classList.add('incorrect');
                block.classList.remove('correct');
            }

            if (!answered.has(questionNum)) {
                answered.add(questionNum);
                updateProgress();
            }
        }

        function updateProgress() {
            const progress = (answered.size / 11) * 100;
            document.getElementById('progress').style.width = progress + '%';
            document.getElementById('answered').textContent = answered.size;
        }

        function downloadHTML() {
            const htmlContent = document.documentElement.outerHTML;
            const blob = new Blob([htmlContent], { type: 'text/html; charset=utf-8' });
            const url = URL.createObjectURL(blob);
            const link = document.createElement('a');
            link.href = url;
            link.download = 'Fragebogen_Marktwirtschaft.html';
            document.body.appendChild(link);
            link.click();
            document.body.removeChild(link);
            URL.revokeObjectURL(url);
        }

        // Event-Listener für alle Multiple-Choice Fragen
        document.addEventListener('DOMContentLoaded', () => {
            const correctAnswers = {
                3: 'Innovation und Effizienz',
                5: 'Investitionen finanzieren und Risiken abdecken',
                6: 'Ein Anbieter kontrolliert den Markt',
                8: 'Bei Marktversagen und zum Schutz von Bürgern',
                11: 'Effizienz, Innovation, Wahlfreiheit'
            };
            
            [3, 5, 6, 8, 11].forEach(questionNum => {
                const radioInputs = document.querySelectorAll(`input[name="q${questionNum}"]`);
                radioInputs.forEach(input => {
                    input.addEventListener('change', () => checkMultiple(questionNum, correctAnswers[questionNum]));
                });
            });
        });

        document.getElementById('total').textContent = '11';
    </script>
</body>
</html>
