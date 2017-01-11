<div align=right><img src="../Tools/imgs/xim.png" ></div>
<h1> Unity SDK FAQ</h1>


**1. How to Get Controllers Positions and Rotations?**

> * You can simply get a reference to a TrackedObject and then grab the transform infomation by using

        public virtual void GetTransform(ref Vector3 position, ref Quaternion rotation);

> * You can also get transform data with ControllerInput class.

        using UnityEngine;
        using Ximmerse;
        using Ximmerse.InputSystem;
      
        class TestClass : MonoBehaviour
        {
            void Update()
            {
                ControllerInput lc = ControllerInputManager.instance.GetControllerInput(ControllerType.LeftController);
      
                Vector3 position = lc.GetPosition();
                Quaternion rotation = lc.GetRotation();
            }
        }

&emsp;

**2.How to Get Head Position and Rotation?**

> It is recommened to use `TrackedHead.target` to grab the head transform information,
because head position requires complex calculation, which is already done in `TrackHead.cs` script.

&emsp;

**3.How to Get Button Press/Down/State?**

> First of all, you need a reference to a `ControllerInput`. Example can be found [here](https://github.com/Ximmerse/SDK/blob/master/Unity/APIDoc.md).

> Then all you need to do is using `GetButton`/`GetButtonUp`/`GetButtonDown` functions implemented in the `ControllerInput` class. Details can be found [here](https://github.com/Ximmerse/SDK/blob/master/Unity/APIDoc.md).
