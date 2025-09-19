# presentacion-interactiva
Presentación interactiva HDAP sobre agua, atmósfera y huracanes.
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { motion, AnimatePresence } from "framer-motion";
import { Droplet, Thermometer, Globe } from "lucide-react";

export default function MegaInteractivePresentationPart2() {
  const slides = [
    // CICLO Y GESTIÓN DEL AGUA (continuación)
    {
      title: "🌧 Recolección de Agua de Lluvia",
      content: "Se recoge el agua de lluvia, se filtra y se almacena para bombearla donde se requiera.",
      icon: <Droplet className="w-16 h-16 mx-auto text-blue-500" />,
    },
    {
      title: "🚰 Distribución del Agua Tratada",
      content: "El agua tratada se bombea a través de tuberías y sistemas de control para mantener flujo y presión.",
      icon: <Droplet className="w-16 h-16 mx-auto text-gray-600" />,
    },
    {
      title: "⚠ Problemática en Veracruz",
      content: "Sequías intensas causan escasez, baja presión y cortes de suministro de agua para miles de personas.",
      icon: <Globe className="w-16 h-16 mx-auto text-red-500" />,
    },
    {
      title: "💡 Medidas Ambientales en Veracruz",
      content: "Programas como ProAire Veracruz y estrategias para conservar la biodiversidad ayudan a reducir el impacto ambiental.",
      icon: <Globe className="w-16 h-16 mx-auto text-teal-500" />,
    },
    {
      title: "🤔 Reflexión sobre el Agua",
      content: "El agua es esencial para la vida. La contaminación, el cambio climático y la sobre explotación la ponen en riesgo. Debemos tomar conciencia y proteger este recurso.",
      icon: <Droplet className="w-16 h-16 mx-auto text-blue-400" />,
    },
    // HURACÁN JOHN
    {
      title: "🌀 Huracán John: Formación y Trayectoria",
      content: "John se originó frente a las costas del Pacífico sur mexicano el 22 de septiembre de 2024 y se intensificó rápidamente hasta categoría 3.",
      icon: <Thermometer className="w-16 h-16 mx-auto text-red-500" />,
    },
    {
      title: "🌪 Intensidad y Duración",
      content: "Vientos máximos de 120 mph (195 km/h) y presión mínima de 956 hPa. Rápida intensificación y trayectoria errática aumentaron el impacto.",
      icon: <Thermometer className="w-16 h-16 mx-auto text-red-500" />,
    },
    {
      title: "🏠 Impacto en Guerrero",
      content: "Al menos 23 muertes, 270,000 personas afectadas. Inundaciones en Acapulco y deslizamientos de tierra en diversas colonias.",
      icon: <Globe className="w-16 h-16 mx-auto text-teal-500" />,
    },
    {
      title: "🌊 Impacto en Oaxaca y Michoacán",
      content: "Desbordamiento de ríos, deslizamientos y daños en infraestructura costera.",
      icon: <Globe className="w-16 h-16 mx-auto text-teal-500" />,
    },
    {
      title: "🛠 Lecciones y Estrategias: Predicción",
      content: "Fortalecer satélites y sistemas de alerta temprana; capacitación en interpretación de datos meteorológicos.",
      icon: <Globe className="w-16 h-16 mx-auto text-blue-500" />,
    },
    {
      title: "🏗 Infraestructura y Planificación",
      content: "Construcción resiliente y zonificación adecuada para resistir eventos climáticos extremos.",
      icon: <Globe className="w-16 h-16 mx-auto text-blue-400" />,
    },
    {
      title: "👥 Participación Comunitaria",
      content: "Programas educativos, simulacros y comités comunitarios de emergencia para preparación ante huracanes.",
      icon: <Globe className="w-16 h-16 mx-auto text-teal-400" />,
    },
    {
      title: "🩺 Respuesta y Recuperación",
      content: "Planes de contingencia, rutas de evacuación, albergues temporales, asistencia médica y apoyo psicológico.",
      icon: <Globe className="w-16 h-16 mx-auto text-blue-500" />,
    },
  ];

  const [index, setIndex] = useState(0);

  const nextSlide = () => {
    if (index < slides.length - 1) setIndex(index + 1);
  };

  const prevSlide = () => {
    if (index > 0) setIndex(index - 1);
  };

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-gradient-to-r from-blue-100 to-green-100 p-6">
      <AnimatePresence mode="wait">
        <motion.div
          key={index}
          initial={{ opacity: 0 }}
          animate={{ opacity: 1 }}
          exit={{ opacity: 0 }}
          transition={{ duration: 0.5 }}
          className="w-full max-w-xl"
        >
          <Card>
            <CardContent className="flex flex-col items-center">
              {slides[index].icon}
              <h2 className="text-2xl font-bold mt-4 mb-2 text-center">{slides[index].title}</h2>
              <p className="text-center text-gray-700">{slides[index].content}</p>
            </CardContent>
          </Card>
        </motion.div>
      </AnimatePresence>
      <div className="flex mt-6 space-x-4">
        <Button onClick={prevSlide} disabled={index === 0}>Anterior</Button>
        <Button onClick={nextSlide} disabled={index === slides.length - 1}>Siguiente</Button>
      </div>
    </div>
  );
}
