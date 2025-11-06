import React, { useState } from 'react';
import { motion } from 'framer-motion';

const collageData = [
  {
    id: 'verse1',
    options: [
      'La lluvia no cae, recuerda.',
      'La lluvia sube desde el suelo.'
    ],
    img: '/images/rain.png',
    initialPos: { x: 50, y: 50 },
  },
  {
    id: 'verse2',
    options: [
      'Mi memoria me miente con ternura.',
      'Mi memoria juega a olvidarme.'
    ],
    img: '/images/memory.png',
    initialPos: { x: 300, y: 100 },
  },
  {
    id: 'verse3',
    options: [
      'Congelo el verso antes del dolor.',
      'El dolor escribe antes que yo.'
    ],
    img: '/images/ice.png',
    initialPos: { x: 180, y: 300 },
  },
];

export default function PoemCollage() {
  const [verses, setVerses] = useState(
    collageData.map((item) => ({ ...item, current: 0, position: item.initialPos }))
  );

  const handleToggle = (index) => {
    setVerses((prev) =>
      prev.map((v, i) =>
        i === index ? { ...v, current: (v.current + 1) % v.options.length } : v
      )
    );
  };

  const handleDrag = (event, info, index) => {
    setVerses((prev) =>
      prev.map((v, i) =>
        i === index ? { ...v, position: { x: info.point.x, y: info.point.y } } : v
      )
    );
  };

  return (
    <div className="relative w-full h-screen bg-neutral-900 overflow-hidden">
      {verses.map((v, i) => (
        <motion.div
          key={v.id}
          className="absolute cursor-move w-64 text-white text-center"
          drag
          dragMomentum={false}
          style={{ top: v.position.y, left: v.position.x }}
          onDragEnd={(event, info) => handleDrag(event, info, i)}
        >
          <img src={v.img} alt="" className="w-full h-32 object-cover rounded-xl opacity-80" />
          <p
            className="mt-2 text-lg font-light hover:opacity-100 opacity-90 hover:text-cyan-300 transition cursor-pointer"
            onClick={() => handleToggle(i)}
          >
            {v.options[v.current]}
          </p>
        </motion.div>
      ))}
    </div>
  );
}
