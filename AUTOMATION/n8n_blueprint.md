# n8n Blueprint (Atlas_OS)

## Workflows (planned)

1. `workflow_sync_identity`
   - Trigger: GitHub commit ใน `L-CORE/` หรือ `PROTOCOL/`
   - Action:
     - ดึงไฟล์ L-CORE.v2 + SPEC
     - เตรียม JSON payload ให้ AI ใช้
   - Output: log + แจ้งเตือน

2. `workflow_sync_tasks`
   - Trigger: แก้ไขไฟล์ใน `W-ROOM/`
   - Action:
     - commit log
     - ส่ง notification (เช่น Line/Telegram)

3. `workflow_AI_request`
   - Trigger: Webhook จาก AI
   - Action:
     - รับคำขอ + room context
     - ดึง identity/protocol ที่เกี่ยวข้อง
     - ส่งกลับเป็น JSON

## Payload Schema (draft)

```json
{
  "user_identity": "from L-CORE/L-CORE.v2.yaml",
  "protocol": "from PROTOCOL/ATLAS_PERSONALITY_OS_SPEC_v1.yaml",
  "room": "L-ROOM | W-ROOM | DNA-ROOM | PROJECT-ROOM",
  "depth": 4
}
