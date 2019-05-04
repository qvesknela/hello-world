using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;








public class GameController : MonoBehaviour
{
    // field variables 

    public float startWait;
    public float cubeWait;
    public GameObject Cubes;
    int range = 1;                                  // aktiuri kubikis diapazoni (shegizlia shecvalo da naxo) 
    int r;                                          // random field
    int num;
    int LastValue;
    List<int> intLst = new List<int>();             // ricxvebis listi
    List<int> rnd = new List<int>();             /// shevkmeni ricxvebis listi


    void Start()
    {
        StartCoroutine(CubeColors());
    }
   
    IEnumerator CubeColors()
    {
        if (range <= 9)                             // 9ze meti rom ar ikos
        {
            yield return new WaitForSeconds(startWait);

            while (true)
            {
                for (int i = 0; i < Cubes.transform.childCount; i++)
                {
                    intLst.Clear();                 // gaasuftave listi
                    rnd.Clear();

                   
                    while (intLst.Count != range)   // sanam listis counti ar ikneba range-is toli koveltvis shesabamisi raodenoba rom ikos
                    {
                        r = Random.Range(0, 9);
                        
                        if (!intLst.Contains(r))    // daamate tu listi ar sheicavs igive cubis nomers
                        {
                          intLst.Add(r);
                        }
                    }
                    Debug.Log(score.scoreValue);
                    for (int l = 0; l < 9; l++) /// gavakete loopi
                    {
                        if (score.scoreValue > LastValue) // sadac sxva scriptidan(score) shemovitane scorevalue tu metia LastValueze
                        {
                            LastValue = score.scoreValue; // udris ertmanets
                        }
                        if (!rnd.Contains(LastValue)) // tu last value arari listshi
                        {
                            rnd.Add(LastValue); /// daamate 
                        }
                    }
                    foreach (var lv in rnd)
                    {
                      //  if (lv) /// aq ver vxvdebi ukve rom es lastValue shemdeg loopze tu igive darcha minda rom gadavides sxva scenaze
                       {

                            SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex + 1); // gadavides sxva scenaze
                       }
                    }
                    foreach (int p in intLst)       // gavaferadot aktiuri cubebi citlad
                    {
                        GameObject child1 = Cubes.transform.GetChild(p).gameObject; 
                        child1.GetComponent<BoxCollider>().enabled = true;
                        child1.GetComponent<SphereCollider>().enabled = false;
                        child1.GetComponent<Renderer>().material.color = Color.red;
                        child1.GetComponent<Animation>().Play("rotation");
                        
                    }

                    for (int x = 0; x < 9; x++)     // kvela cubistvis 
                    {
                        if (!intLst.Contains(x))    // tu is ar udris archeul aktiur cubebs vaferadebt lurjad
                        {
                            GameObject child2 = Cubes.transform.GetChild(x).gameObject; 
                            child2.GetComponent<BoxCollider>().enabled = false;
                            child2.GetComponent<SphereCollider>().enabled = true;
                            child2.GetComponent<Renderer>().material.color = Color.white;
                        }
                    }
                    yield return new WaitForSeconds(cubeWait);
                }
            }

        }
    }

    
}
