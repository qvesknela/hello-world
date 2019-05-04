 bbbbb
           
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
                    for (int l = 0; l < 9; l++)
                    {
                        if (score.scoreValue > LastValue)
                        {
                            LastValue = score.scoreValue;
                        }
                        if (!rnd.Contains(LastValue))
                        {
                            rnd.Add(LastValue);
                        }
                    }
                    foreach (var lv in rnd)
                    {
                      //  if (lv)
                       // {

                       //     SceneManager.LoadScene(SceneManager.GetActiveScene().buildIndex + 1);
                      //  }
                    }
