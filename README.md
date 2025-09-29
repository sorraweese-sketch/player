public class PlayerMovement : MonoBehaviour
{
    public float moveSpeed = 5f;   // ความเร็วเดิน
    public float runSpeed = 10f;   // ความเร็ววิ่ง
    private float speed;

    private Rigidbody rb;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
        speed = moveSpeed; // เริ่มต้นที่ความเร็วเดิน
    }

    void Update()
    {
        // รับค่าการกดปุ่ม (WASD / ลูกศร)
        float moveX = Input.GetAxis("Horizontal");
        float moveZ = Input.GetAxis("Vertical");

        Vector3 move = new Vector3(moveX, 0f, moveZ).normalized;

        // กด Shift ซ้ายเพื่อวิ่ง
        if (Input.GetKey(KeyCode.LeftShift))
        {
            speed = runSpeed;
        }
        else
        {
            speed = moveSpeed;
        }

        // เคลื่อนที่
        Vector3 newPos = rb.position + move * speed * Time.deltaTime;
        rb.MovePosition(newPos);
    }
}
