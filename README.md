# tiemtruyennho
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";

export default function StoryPage() {
  const chapters = [
    { id: 1, title: "Chương 1", content: "Nội dung chương 1" },
    { id: 2, title: "Chương 2", content: "Nội dung chương 2", locked: true },
    { id: 3, title: "Chương 3", content: "Nội dung chương 3" },
    { id: 4, title: "Chương 4", content: "Nội dung chương 4", locked: true },
    { id: 5, title: "Chương 5", content: "Nội dung chương 5" },
    { id: 6, title: "Chương 6", content: "Nội dung chương 6", locked: true },
  ];

  const [unlockedChapters, setUnlockedChapters] = useState([]);

  const handleUnlock = (id) => {
    // Thay link này bằng link thật của m
    window.open("https://example.com", "_blank");
    setTimeout(() => {
      setUnlockedChapters([...unlockedChapters, id]);
    }, 1000);
  };

  return (
    <div className="p-4 max-w-2xl mx-auto">
      <h1 className="text-2xl font-bold mb-4">Truyện của bạn</h1>
      {chapters.map((chapter) => (
        <Card key={chapter.id} className="mb-4">
          <CardContent className="p-4">
            <h2 className="text-xl font-semibold">{chapter.title}</h2>
            {chapter.locked && !unlockedChapters.includes(chapter.id) ? (
              <Button onClick={() => handleUnlock(chapter.id)} className="mt-2">
                Nhấp vào link để mở khóa
              </Button>
            ) : (
              <p className="mt-2">{chapter.content}</p>
            )}
          </CardContent>
        </Card>
      ))}
    </div>
  );
}
