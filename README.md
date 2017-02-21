# Unity-Beat-Detection
Musical beat detection and audio spectrum analysis for use with the Unity game engine.

The AudioProcessor class contains an interface that can be implemented on your GameObject.

<h2>Usage</h2>
Add the AudioProcessor script to your <b>Main Camera</b> object and 
adjust the <b>threshold</b> parameter to change the sensitivity. 
Then set a callback delegate on the audio processor's <b>onBeat</b> or <b>onSpectrum</b> events.

```c#
public class Example : MonoBehaviour
{
    
	void Start ()
	{
		//Select the instance of AudioProcessor and pass a reference
		//to this object
		AudioProcessor processor = FindObjectOfType<AudioProcessor> ();
		processor.onBeat.AddListener (onOnbeatDetected);
		processor.onSpectrum.AddListener (onSpectrum);
	}

	//this event will be called every time a beat is detected.
	//Change the threshold parameter in the inspector
	//to adjust the sensitivity
	void onOnbeatDetected ()
	{
		Debug.Log ("Beat!!!");
	}

	//This event will be called every frame while music is playing
	void onSpectrum (float[] spectrum)
	{
		//The spectrum is logarithmically averaged
		//to 12 bands

		for (int i = 0; i < spectrum.Length; ++i) {
			Vector3 start = new Vector3 (i, 0, 0);
			Vector3 end = new Vector3 (i, spectrum [i], 0);
			Debug.DrawLine (start, end);
		}
	}
}
```
