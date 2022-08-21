---
title: Rigidbody.MoveRotation <Wrong>
categories: [Rigidbody, Rotation]
tags: [unity] #lowercase
---

# Rigidbody GameObject Rotate 에러   

　　　　　　　　　　　　　　　　　　　　　　　　
　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　
　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　　
　
　



# 다시 해보니 동작한다. 😝   
----------------------------------------
```csharp
float moveSpeed = 5.0f;
Vector3 moveVec = new Vector3(x, 0, z) * moveSpeed * Time.fixedDeltaTime;
Quaternion dirQuat = Quaternion.LookRotation(moveVec);
Quaternion moveQuat = Quaternion.Slerp(rb.rotation, dirQuat, 0.3f);
rb.MoveRotation(moveQuat);

// Rigidbody rb = GetComponent<Rigidbody>()
```
~~위 코드는 rigid body가 있는 오브젝트를 회전할때 사용 할 수 있지만
해당 오브젝트의 rigidbody가 
구형(Shpere)인 경우 MoveRotation이 작동하지 않는다.~~


----------------------------------------


# Rotates the rigidbody to rotation.

Use Rigidbody.MoveRotation to rotate a Rigidbody, complying with the Rigidbody's interpolation setting.

If Rigidbody interpolation is enabled on the Rigidbody, calling Rigidbody.MoveRotation will resulting in a smooth transition between the two positions in any intermediate frames rendered. This should be used if you want to continuously rotate a rigidbody in each FixedUpdate.

Set Rigidbody.rotation instead, if you want to teleport a rigidbody from one rotation to another, with no intermediate positions being rendered.


----------------------------------------

```csharp
using UnityEngine;
using System.Collections;

public class ExampleClass : MonoBehaviour {
    public Vector3 eulerAngleVelocity;
    public Rigidbody rb;
    void Start() {
        rb = GetComponent<Rigidbody>();
    }
    void FixedUpdate() {
        Quaternion deltaRotation = Quaternion.Euler(eulerAngleVelocity * Time.deltaTime);
        rb.MoveRotation(rb.rotation * deltaRotation);
    }
}

```

----------------------------------------

# 사용처
## 조이스틱을 사용하여 오브젝트를 움직이고
## 움직이는 방향으로 바라보게(회전)시키는 코드 

```csharp


public class PlayerMove : MonoBehaviour
{
    //public FixedJoystick joystick;
    public VariableJoystick varJoystick;

    public float moveSpeed;

    Rigidbody rb;
    Animator anitr;
    Vector3 moveVec;

    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody>();
        anitr = GetComponent<Animator>();

        
    }

    private void FixedUpdate()
    {
        float x = varJoystick.Horizontal;
        float z = varJoystick.Vertical;
        
        moveVec = new Vector3(x, 0, z) * moveSpeed * Time.fixedDeltaTime;
        rb.MovePosition(rb.position + moveVec);

        if (moveVec.sqrMagnitude == 0)
            return; // NO INPUT = NO ROTATION

        Debug.Log("Rotation");
        Quaternion dirQuat = Quaternion.LookRotation(moveVec);
        Quaternion moveQuat = Quaternion.Slerp(rb.rotation, dirQuat, 0.3f);
        rb.MoveRotation(moveQuat);
        
    }

    private void LateUpdate()
    {
        //anitr.SetFloat("PlayerMove", moveVec.sqrMagnitude);
    }

    // Update is called once per frame
    void Update()
    {
        
    }
}


```



----------------------------------------
[참고]

[조이스틱](https://www.youtube.com/watch?v=GGqwMGZiwCg&ab_channel=%EA%B3%A8%EB%93%9C%EB%A9%94%ED%83%88)
