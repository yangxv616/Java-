# Comparable接口
**源码**：

	public interface Comparable<T>
	{
		int compareTo(T other);
	}
	
	调用x.compareTo(y)时，若x<y,则返回一个负数，若x=y则返回0，若x>y则返回一个正数。