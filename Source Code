using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CubeManager : MonoBehaviour
{
    public GameObject CubePiece;
    public int speed;
    Transform CubeTrans;
    List<GameObject> AllCubePieces = new List<GameObject>();
    GameObject CubeCenter;
   bool canRotate = true;
    bool leftShift = false;

    List<GameObject> UpPieces
    {
        get
        {
            return AllCubePieces.FindAll(x => Mathf.Round(x.transform.localPosition.y) == 2);
        }
    }

    List<GameObject> DownPieces
    {
        get
        {
            return AllCubePieces.FindAll(x => Mathf.Round(x.transform.localPosition.y) == 0);
        }
    }

    List<GameObject> FrontPieces
    {
        get
        {
            return AllCubePieces.FindAll(x => Mathf.Round(x.transform.localPosition.z) == 2);
        }
    }

    List<GameObject> BackPieces
    {
        get
        {
            return AllCubePieces.FindAll(x => Mathf.Round(x.transform.localPosition.z) == 0);
        }
    }

    List<GameObject> RightPieces
    {
        get
        {
            return AllCubePieces.FindAll(x => Mathf.Round(x.transform.localPosition.x) == 0);
        }
    }

    List<GameObject> LeftPieces
    {
        get
        {
            return AllCubePieces.FindAll(x => Mathf.Round(x.transform.localPosition.x) == 2);
        }
    }


    void Start()
    {
        CreateCube();
    }


    void Update()
    {
        if (canRotate)
        {
            if (Input.GetKey(KeyCode.LeftShift))
            {
                leftShift = true;
            }
            else
            {
                leftShift = false;
            }
            CheckInput();
        }

    }

    void CreateCube()
    {
        for (int x = 0; x < 3; x++)
        {
            for (int y = 0; y < 3; y++)
            {
                for (int z = 0; z < 3; z++)
                {
                    GameObject go = Instantiate(CubePiece, CubeTrans, false);
                    go.transform.localPosition = new Vector3(x, y, z);

                    AllCubePieces.Add(go);
                }
            }
        }
        CubeCenter = AllCubePieces[13];
    }

    void CheckInput()
    {
        if (Input.GetKeyDown(KeyCode.Z))
        {
            if (leftShift)
            {
              StartCoroutine(Rotate(AllCubePieces, new Vector3(0, -1, 0)));
            }
            else
            {
                StartCoroutine(Rotate(AllCubePieces, new Vector3(0, 1, 0)));
            }
        }
        if (Input.GetKeyDown(KeyCode.X))
        {
            if (leftShift)
            {
                StartCoroutine(Rotate(AllCubePieces, new Vector3(1, 0, 0)));
            }
            else
            {
                StartCoroutine(Rotate(AllCubePieces, new Vector3(-1, 0, 0)));
            }
        }
        if (Input.GetKeyDown(KeyCode.C))
        {
            if (leftShift)
            {
                StartCoroutine(Rotate(AllCubePieces, new Vector3(0,0 , -1)));
            }
            else
            {
                StartCoroutine(Rotate(AllCubePieces, new Vector3(0,0 , 1)));
            }
        }

        if (Input.GetKeyDown(KeyCode.W))
        {
            if (leftShift)
            {
                StartCoroutine(Rotate(UpPieces, new Vector3(0, -1, 0)));
            }
            else
            {
                StartCoroutine(Rotate(UpPieces, new Vector3(0, 1, 0)));
            }
        }

        else if (Input.GetKeyDown(KeyCode.S))
        {
            if (leftShift)
            {
                StartCoroutine(Rotate(DownPieces, new Vector3(0, 1, 0)));
            }
            else
            {
                StartCoroutine(Rotate(DownPieces, new Vector3(0, -1, 0)));
            }
        }

        else if (Input.GetKeyDown(KeyCode.E))
        {
            if (leftShift)
            {
                StartCoroutine(Rotate(FrontPieces, new Vector3(0, 0, -1)));
            }
            else
            {
                StartCoroutine(Rotate(FrontPieces, new Vector3(0, 0, 1)));
            }
        }

        else if (Input.GetKeyDown(KeyCode.Q))
        {
            if (leftShift)
            {
                StartCoroutine(Rotate(BackPieces, new Vector3(0, 0, 1)));
            }
            else
            {
                StartCoroutine(Rotate(BackPieces, new Vector3(0, 0, -1)));
            }
        }

        else if (Input.GetKeyDown(KeyCode.D))
        {
            if (leftShift)
            {
                StartCoroutine(Rotate(RightPieces, new Vector3(1, 0, 0)));
            }
            else
            {
                StartCoroutine(Rotate(RightPieces, new Vector3(-1, 0, 0)));
            }
        }

        else if (Input.GetKeyDown(KeyCode.A))
        {
            if (leftShift)
            {
                StartCoroutine(Rotate(LeftPieces, new Vector3(-1, 0, 0)));
            }
            else
            {
                StartCoroutine(Rotate(LeftPieces, new Vector3(1, 0, 0)));
            }
        }

    }

    IEnumerator Rotate(List<GameObject> pieces, Vector3 rotationVec)
    {
       canRotate = false;
        int angle = 0;

        while (angle < 90)
        {
            foreach (GameObject go in pieces)
                go.transform.RotateAround(CubeCenter.transform.position, rotationVec, speed);
            angle += speed;
            yield return null;
        }
        canRotate = true;
    }


}
