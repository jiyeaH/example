### OCR 예제
Java Programing ex
```java
import java.util.Calendar;

public class ocr_checkpoint316 {

	public static boolean IS_TEST = true; //False는 real time
	
	public static void main(String[] args) {
		// TODO Auto-generated method stub

		TimeReminder rt = new TimeReminder();
		
		TimeProvider tp;
		if(!IS_TEST) {
			tp = new RealTimeProvider();
		}
		else
		{
			tp = new FakeTimeProvider();
		}
		
		
		rt.setTimeProvider(tp);
		rt.reminder(new MP3());
		
	}

}

interface TimeProvider
{
	public int getTime();
	
}

class RealTimeProvider implements TimeProvider {
	Calendar cal;
	@Override
	public int getTime() {
		// TODO Auto-generated method stub
		cal = Calendar.getInstance();
		return cal.get(Calendar.HOUR_OF_DAY);
	}
	
}

class FakeTimeProvider implements TimeProvider {

	@Override
	public int getTime() {
		// TODO Auto-generated method stub
		return 22; //10시에 대한 시간을 얻도록.
	}
	
}

class TimeReminder {
	TimeProvider tp;
	
	public void setTimeProvider(TimeProvider tp)
	{
		this.tp = tp;
	}
	public void reminder(MP3 m)
	{
		if(tp.getTime() >= 22)
		{
			m.playSong();
		}
		else {
			System.out.println("아직 22시가 아닙니다.");
		}
	}
}

class MP3 {
	public void playSong() 
	{
		System.out.println("Play MP3");
	}
}
```
