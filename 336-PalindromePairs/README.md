## ��Ŀ������

����һ���ַ�������`words`�����ظ��ַ������ʣ��ж��ٶԲ�ͬ��`(i, j)`����`words[i]+words[j]`�ǻ��Ĵ���

### ����˼·��1��
����ö��`(i, j)`���ж�`words[i]+words[j]`�Ƿ��ǻ��Ĵ���ʱ�临�Ӷ�Ϊ`O(n^2*k)`��
### ����˼·��2��
�������ַ����������`map`������ÿ���ַ���`s`��ö�ٷָ��`pos`������`[pos ~ s.size()-1]`�ǻ��Ĵ�����`[0 ~ pos-1]`���洮��`map`�д��ڡ�ʱ�临�Ӷ�Ϊ`O(n*K)`��
#### �㷨����ȷ�ԣ�
˼·1�������������˼·2����`words = ["bat", "tab", "cat"]`�� ��`map["tab"] = 0`, `map["bat"] = 1`, `map["tac"] = 2`, ����`"bat"`, ���Ƿ���`map["bat"] = 1`����ĩβ��`""`Ϊ���Ĵ�����`(0, 1)`Ϊһ�⣻����`"bat"`, ���Ƿ���`map["tab"] = 0`����ĩβ��`""`Ϊ���Ĵ�����`(1, 0)`Ϊһ�⡣�ʴ�Ϊ`[[0, 1], [1, 0]]`��