# ruleta-psicologia-sistematica.io
ruleta sistematica
import React, { useEffect, useRef, useState } from "react";
className="border rounded px-2 py-1"
value={playerName}
onChange={(e) => setPlayerName(e.target.value)}
placeholder="Tu nombre"
/>
<button onClick={spinWheel} className="px-4 py-2 bg-indigo-600 text-white rounded shadow hover:bg-indigo-700" disabled={spinning || questions.length===0}>
{spinning ? "Girando..." : "Girar ruleta"}
</button>
<button onClick={resetGame} className="px-4 py-2 bg-gray-200 rounded">Reset</button>
</div>


<div className="mt-3 text-sm text-gray-700">Puntos actuales: <span className="font-semibold">{score}</span></div>
</section>


<aside className="w-full md:w-80 bg-white rounded-2xl p-4 shadow">
<h2 className="font-semibold text-lg">Podio — Top 3</h2>
<ol className="mt-3 space-y-2">
{leaderboard.slice(0, 3).map((p, idx) => (
<li key={p.name} className="flex items-center gap-3">
<div className={`w-10 h-10 rounded-full flex items-center justify-center text-white font-bold ${idx===0?"bg-yellow-400": idx===1?"bg-gray-300":"bg-amber-700"}`}>
{idx+1}
</div>
<div className="flex-1">
<div className="font-medium">{p.name}</div>
<div className="text-sm text-gray-500">{p.score} pts</div>
</div>
</li>
))}
{leaderboard.length===0 && <div className="text-sm text-gray-500 mt-2">Aún no hay puntuaciones. Juega y entra al podio.</div>}
</ol>


<hr className="my-3" />


<div>
<h3 className="font-medium">Top 10</h3>
<ul className="text-sm mt-2 space-y-1 max-h-40 overflow-auto">
{leaderboard.map((p) => (
<li key={p.name} className="flex justify-between">
<span>{p.name}</span>
<span className="font-semibold">{p.score}</span>
</li>
))}
</ul>
</div>


<div className="mt-4 text-xs text-gray-500">Los puntajes se guardan en tu navegador (localStorage).</div>
</aside>
</main>


{/* Modal de pregunta */}
{showQuestionModal && currentQuestion && (
<div className="fixed inset-0 bg-black/40 flex items-center justify-center p-4">
<div className="bg-white rounded-xl shadow-xl max-w-2xl w-full p-6">
<h3 className="text-xl font-bold text-indigo-700">Pregunta</h3>
<p className="mt-2 text-gray-700">{currentQuestion.pregunta}</p>


<div className="mt-4 grid gap-3">
{currentQuestion.opciones.map((opt, i) => (
<button key={i} onClick={() => answerQuestion(i)} className="text-left p-3 border rounded hover:shadow">
<span className="font-medium">{String.fromCharCode(65 + i)}. </span>
<span>{opt}</span>
</button>
))}
</div>


<div className="mt-4 flex justify-end gap-2">
<button onClick={() => { setShowQuestionModal(false); setCurrentQuestion(null); }} className="px-3 py-1 border rounded">Cerrar</button>
</div>
</div>
</div>
)}


<footer className="text-xs text-gray-500 mt-6">Plantilla creada para uso educativo — puedes editar las preguntas desde el código.</footer>
</div>
);
}                
