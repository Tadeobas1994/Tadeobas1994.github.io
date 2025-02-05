import { useState, useEffect } from "react";
import { Card } from "@/components/ui/card";
import Image from "next/image";

export default function DogeValentine() {
  const targetDate = new Date("February 14, 2025 00:00:00").getTime();
  const [timeLeft, setTimeLeft] = useState(targetDate - new Date().getTime());

  useEffect(() => {
    const interval = setInterval(() => {
      setTimeLeft(targetDate - new Date().getTime());
    }, 1000);
    return () => clearInterval(interval);
  }, []);

  const formatTime = (ms) => {
    const seconds = Math.floor((ms / 1000) % 60);
    const minutes = Math.floor((ms / 1000 / 60) % 60);
    const hours = Math.floor((ms / (1000 * 60 * 60)) % 24);
    const days = Math.floor(ms / (1000 * 60 * 60 * 24));
    return `${days}d ${hours}h ${minutes}m ${seconds}s`;
  };

  return (
    <div className="flex flex-col items-center justify-center min-h-screen bg-pink-100 text-center">
      <Card className="p-6 shadow-lg rounded-2xl bg-white">
        <Image 
          src="/dogevalentine_logo.png" 
          alt="DogeValentine Logo" 
          width={200} 
          height={200} 
          className="rounded-full mb-4"
        />
        <h1 className="text-3xl font-bold text-pink-600">Welcome to DogeValentine!</h1>
        <p className="text-lg text-gray-600">Join the ultimate meme-coin community and ride the love wave to profits!</p>
        <div className="mt-4 text-2xl font-semibold text-red-500">
          Countdown to Valentine's Day: {formatTime(timeLeft)}
        </div>
        <p className="mt-4 text-gray-500">Don’t miss out on the most romantic crypto event of the year!</p>
      </Card>
    </div>
  );
}
