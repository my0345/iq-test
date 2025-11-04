const questions = [
  {
    question: "Who developed Java?",
    answers: [
      { text: "James Gosling", correct: true },
      { text: "Dennis Ritchie", correct: false },
      { text: "Bjarne Stroustrup", correct: false },
      { text: "Guido van Rossum", correct: false }
    ]
  },
  {
    question: "Which company first released Java?",
    answers: [
      { text: "Sun Microsystems", correct: true },
      { text: "Microsoft", correct: false },
      { text: "Oracle", correct: false },
      { text: "IBM", correct: false }
    ]
  },
  {
    question: "Which keyword is used to inherit a class in Java?",
    answers: [
      { text: "this", correct: false },
      { text: "extends", correct: true },
      { text: "implements", correct: false },
      { text: "import", correct: false }
    ]
  },
  {
    question: "What is the default value of a boolean variable?",
    answers: [
      { text: "0", correct: false },
      { text: "1", correct: false },
      { text: "true", correct: false },
      { text: "false", correct: true }
    ]
  },
  {
    question: "Which of these is not a Java feature?",
    answers: [
      { text: "Object-oriented", correct: false },
      { text: "Platform-independent", correct: false },
      { text: "Use of pointers", correct: true },
      { text: "Secure", correct: false }
    ]
  }
];

const questionElement = document.getElementById("question");
const answerButtons = document.getElementById("answer-buttons");
const nextButton = document.getElementById("next-btn");

let currentQuestionIndex = 0;
let score = 0;

function startQuiz() {
  currentQuestionIndex = 0;
  score = 0;
  nextButton.innerHTML = "Next";
  showQuestion();
}

function showQuestion() {
  resetState();
  let currentQuestion = questions[currentQuestionIndex];
  let questionNo = currentQuestionIndex + 1;
  questionElement.innerHTML = questionNo + ". " + currentQuestion.question;

  currentQuestion.answers.forEach(answer => {
    const button = document.createElement("button");
    button.innerHTML = answer.text;
    button.classList.add("btn");
    answerButtons.appendChild(button);
    if (answer.correct) {
      button.dataset.correct = answer.correct;
    }
    button.addEventListener("click", selectAnswer);
  });
}

function resetState() {
  nextButton.style.display = "none";
  while (answerButtons.firstChild) {
    answerButtons.removeChild(answerButtons.firstChild);
  }
}

function selectAnswer(e) {
  const selectedBtn = e.target;
  const isCorrect = selectedBtn.dataset.correct === "true";
  if (isCorrect) {
    selectedBtn.classList.add("correct");
    score++;
  } else {
    selectedBtn.classList.add("wrong");
  }

  Array.from(answerButtons.children).forEach(button => {
    if (button.dataset.correct === "true") {
      button.classList.add("correct");
    }
    button.disabled = true;
  });

  nextButton.style.display = "block";
}

function showScore() {
  resetState();
  questionElement.innerHTML =` You scored ${score} out of ${questions.length}! 🎉`;
  nextButton.innerHTML = "Play Again";
  nextButton.style.display = "block";
}

function handleNextButton() {
  currentQuestionIndex++;
  if (currentQuestionIndex < questions.length) {
    showQuestion();
  } else {
    showScore();
  }
}

nextButton.addEventListener("click", () => {
  if (currentQuestionIndex < questions.length) {
    handleNextButton();
  } else {
    startQuiz();
  }
});

startQuiz();