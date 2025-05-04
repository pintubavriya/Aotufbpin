import React, { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";
import { Textarea } from "@/components/ui/textarea";
import { Calendar } from "@/components/ui/calendar";
import { Checkbox } from "@/components/ui/checkbox";
import { Label } from "@/components/ui/label";

export default function AutopinFBDashboard() {
  const [caption, setCaption] = useState("");
  const [file, setFile] = useState(null);
  const [pages, setPages] = useState({ page1: false, page2: false });
  const [date, setDate] = useState(new Date());

  const handleUpload = () => {
    // Placeholder function for handling upload
    alert("Upload scheduled!");
  };

  return (
    <div className="p-4 grid gap-4 max-w-xl mx-auto">
      <h1 className="text-2xl font-bold">AutopinFB - Auto Upload Dashboard</h1>

      <Card>
        <CardContent className="grid gap-4 p-4">
          <Input type="file" onChange={(e) => setFile(e.target.files[0])} />

          <Textarea
            placeholder="Enter caption..."
            value={caption}
            onChange={(e) => setCaption(e.target.value)}
          />

          <div className="grid gap-2">
            <Label>Select Facebook Pages:</Label>
            <div className="flex gap-4">
              <div className="flex items-center gap-2">
                <Checkbox
                  checked={pages.page1}
                  onCheckedChange={(val) =>
                    setPages({ ...pages, page1: val })
                  }
                />
                <Label>Page 1</Label>
              </div>
              <div className="flex items-center gap-2">
                <Checkbox
                  checked={pages.page2}
                  onCheckedChange={(val) =>
                    setPages({ ...pages, page2: val })
                  }
                />
                <Label>Page 2</Label>
              </div>
            </div>
          </div>

          <div className="grid gap-2">
            <Label>Schedule Post:</Label>
            <Calendar mode="single" selected={date} onSelect={setDate} />
          </div>

          <Button onClick={handleUpload}>Schedule Upload</Button>
        </CardContent>
      </Card>
    </div>
  );
}

