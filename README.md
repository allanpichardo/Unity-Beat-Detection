# Unity-Beat-Detection
Musical beat detection and audio spectrum analysis for use with the Unity game engine.

The AudioProcessor class contains an interface that can be implemented on your GameObject.

<h2>Usage</h2>
Add the AudioProcessor script to your <b>Main Camera</b> object and 
adjust the <b>threshold</b> parameter to change the sensitivity. 
Then simply implement the <b>AudioCallbacks</b> interface on any object you'd like
to be notified when a beat is detected.

```c#
public class Example : MonoBehaviour, AudioProcessor.AudioCallbacks{
void Start()
    {
        //Select the instance of AudioProcessor and pass a reference
        //to this object
        AudioProcessor processor = FindObjectOfType<AudioProcessor>();
        processor.addAudioCallback(this);
    }

    
    void Update()
    {
        
    }

    public void onOnbeatDetected()
    {
        Debug.Log("Beat!!!");
    }

    public void onSpectrum(float[] spectrum)
    {
       
    }
}
```
