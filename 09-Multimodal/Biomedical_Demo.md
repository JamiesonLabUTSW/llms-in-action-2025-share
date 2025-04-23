# Neurological Examination Video Analysis: Prompt Demos

This file contains prompt demonstrations for using a multimodal clinical-video analysis assistant to interpret neurological examination recordings, organized as follows:

1. **Purpose:** Demonstrate the assistant’s capability to analyze comprehensive neurological exam videos.
2. **Components:** Includes a System Prompt and four User Prompts.
3. **User Prompts:**
   - Zero‑Shot General Neurological Exam
   - Gait Examination Focus
   - Eye Examination Focus
   - Confrontation Visual Fields (Left and Right Eye)
4. **Method:** Leverage both visual and audio cues from the video to inform segmentation, classification, and explanation.

To follow along with an example neurological examination scenario, you can refer to this sample video on YouTube:

[https://www.youtube.com/watch?v=q56WgXvn0iU](https://www.youtube.com/watch?v=q56WgXvn0iU)

Video Selection Rationale: This video was chosen because it does not have on-screen text overlays, challenging the assistant to rely entirely on multimodal analysis.

---

## System Prompt
```text
You are a multimodal clinical‑video analysis assistant trained to interpret neurological examination recordings. When given a neurological examination video, you should:

1. Leverage both visual and audio cues from the video to identify and timestamp each examination segment.
2. Segment Identification
   - Detect and timestamp each distinct neurological examination segment in the video (HH:MM:SS).
3. Exam Classification
   - Label each segment with the specific type of neurological exam being performed.
4. Doctor Instructions
   - Transcribe or summarize any instructions the doctor gives to the patient during that segment.
5. Detailed Explanation
   - Describe step by step what the examiner is doing, why each maneuver is performed, and what findings are sought.

Structure your response for each exam with these headings:

Exam Type:
Start Time:
End Time:
Doctor Instructions:
Detailed Explanation:
```
*Explanation:* This system prompt guides the assistant to use both audio and visual information to accurately segment, classify, and detail each neurological examination maneuver, ensuring comprehensive analysis of the video.

---

## Demo 1: Zero‑Shot General Neurological Exam
```text
Analyze the following neurological examination video and provide a comprehensive breakdown of every neurological examination performed. For each exam segment, identify:
- Exam Type
- Start Time and End Time (HH:MM:SS)
- Doctor Instructions given to the patient
- A Detailed Explanation of each step in the exam procedure

Use visual and audio cues from the video to determine the exam types, timestamps, instructions, and explanations.
```
*Explanation:* This zero‑shot prompt challenges the assistant to detect and describe all neurological exam segments without prior examples, showcasing its ability to generalize across varied content.

---

## Demo 2: Gait Examination Focus
```text
In this neurological examination video, focus exclusively on all gait examinations. For each gait assessment performed:
- Specify the type of gait examination
- Provide the start and end timestamps (HH:MM:SS)
- Describe what is happening during each assessment in detail
- List any instructions the doctor gives to the patient

Use visual and audio cues from the video to determine the gait types, timings, and instructions.
```
*Explanation:* This prompt narrows the scope to gait assessments, enabling targeted analysis of walking and balance tests within a neurological exam, including timestamps, patient actions, and examiner cues.

---

## Demo 3: Eye Examination Focus
```text
Analyze the following neurological examination video segment and identify every eye examination performed:
- Exam Type
- Start Time and End Time (HH:MM:SS)
- Doctor Instructions given
- A Detailed Explanation of the examination maneuvers and what the examiner is assessing

Use visual and audio cues from the video to determine the eye exam types, timestamps, and instructions.
```
*Explanation:* This focused prompt directs the assistant to dissect ocular assessments in a neurological context, detailing each maneuver, its clinical purpose, and the patient’s compliance as observed through multimodal cues.

---

## Demo 4: Confrontation Visual Fields (Left and Right Eye Separately)
```text
Analyze the following neurological examination video and identify left eye and right eye confrontation visual fields examinations separately. For each:
- Eye (Left or Right)
- Exam Type: Confrontation Visual Fields
- Start Time and End Time (HH:MM:SS)
- Doctor Instructions given
- Detailed Explanation of the maneuver and what is being assessed

Use visual and audio cues from the video to determine the eye, timings, instructions, and findings.
```
*Explanation:* This prompt instructs the assistant to distinguish and detail the confrontation visual fields examination for each eye separately in a neurological exam, including timestamps, instructions, and observations.*

