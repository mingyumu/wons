�ֻ�����������������ģʽ������

adb reboot bootloader

��������Զ�����fastbootģʽ

���ţ�

fastboot devices

�鿴�Ƿ����豸



//erase ��������˼���㶮��

fastboot erase system
fastboot erase cache
fastboot erase config
fastboot erase data
fastboot erase logs
fastboot erase factory


fastboot flash boot boot.img

fastboot flash system system.img

fastboot flash recovery recovery.img

fastboot boot recoveryout.img


fastboot reboot

����


Android ADB ��������
[TOC]

adb logcat �鿴��־
��ϸ���ݿɲμ�

ADB Usage Complete / ADB �÷���ȫ

�ٷ��ĵ� Listing of logcat Command Options

�������� http://jiongbull.com/2016/03/17/adb%E5%91%BD%E4%BB%A4/

Ӧ�����
�鿴Ӧ���б�
adb shell pm list package
# has root
adb shell ls /data/data/
adb ���� / ֹͣ Ӧ�ó���
adb shell am start -n [packageName/StartActivity]
adb shell am force-stop [packageName]
�˿�ӳ��
# ��ʾ����(PC ��> DEVICE)ӳ��Ķ˿������б�
adb forward ��list
# ӳ��˿�����(PC ��> DEVICE)
adb forward (local) (remote)
adb forward tcp:6100 tcp:7100
# ӳ��˿����ӣ��������local�Ѿ�ӳ���˾ͻ�ʧ��
adb forward ��no-rebind (local) (remote)
adb forward --no-rebind tcp:6100 tcp:7100
# �Ƴ�ָ����ӳ��˿�����
adb forward ��remove tcp:6100
# �Ƴ����е�ӳ��˿�����
adb forward ��remove-all
# ��ʾ���������豸��(DEVICE ��> PC)ӳ��Ķ˿������б�
adb reverse ��list
# ����ӳ��˿�����(DEVICE ��> PC)
adb reverse (remote) (local)
adb reverse tcp:7000 tcp:5000
# ���local�Ѿ�ӳ���˾ͻ�ʧ��
adb reverse ��no-rebind (remote) (local)
adb reverse --no-rebind tcp:7000 tcp:5000
# �Ƴ�ָ���ķ���ӳ��˿�����
adb reverse ��remove tcp:7000
adb reverse ��remove-all
Ӧ�ð�װж��
# ��ȡapk��packagename �� classname
aapt d badging <apkfile>
# ��װapk
adb install <apkfile>
# �������ݺͻ����ļ������°�װapk��
adb install -r <apkfile>
# ��װapk��sd��
adb install -s <apkfile>
# ж��app
adb uninstall <package>
# ж��app���������ݺͻ����ļ�
adb uninstall -k <package>
# ͬʱ��װ�����apk���豸��
adb install-multiple
adb install ����

-l ����Ӧ��
-r �滻�Ѵ��ڵ�Ӧ��
-t ����װ���԰�
-s ��װ�� sd ����
-d ���԰�װ�Ͱ汾��װ��
-p ��װ����Ӧ��
-g ��Ȩ��������ʱȨ��
Ӧ��״̬�鿴
# �鿴�����б�
adb shell ps
# �鿴ָ������״̬
adb shell ps -x [PID]
# �鿴��̨services��Ϣ
adb shell service list
# �鿴IO�ڴ����
adb shell cat /proc/iomem
���Բ鿴
�г�����ӵ�� JDWP �˿ڽ��̵Ľ��̺�

adb jdwp
�ļ�����
# �鿴���д洢�豸��
adb shell ls mnt
# �ӱ��ظ����ļ����豸
adb push <local> <remote>
# ���豸�����ļ�������
adb pull <remote>  <local>
# �г�Ŀ¼�µ��ļ����ļ��У���ͬ��dos�е�dir����
adb shell ls
# �����ļ��У���ͬ��dos�е�cd ����
adb shell cd <folder>
# �������ļ�
adb shell rename path/oldfilename path/newfilename
# ɾ��system/avi.apk
adb shell rm /system/avi.apk
# ɾ���ļ��м������������ļ�
adb shell rm -r <folder>
# �ƶ��ļ�
adb shell mv path/file newpath/file
# �����ļ�Ȩ��
adb shell chmod 777 [filePath]
# �½��ļ���
adb shell mkdir -d path/foldelname
adb sync
�� Android �豸��/system��/dataĿ¼��������Ŀ¼�в�һ�µ�����ͬ���������ϡ�
ʹ��ǰ��Ҫ��������Ŀ¼��ַ�Ļ���������

adb sync(δ���û�������)

D:\Code\Git>adb sync
adb: Product directory not specified; use -p or define ANDROID_PRODUCT_OUT
set ANDROID_PRODUCT_OUT = (PATH)

D:\Code\Git>set ANDROID_PRODUCT_OUT = D:\Data\Android
adb sync(�����û�������)

D:\Code\Git>adb sync
syncing /system...
push: D:\Data\Android\system/app/WAPPushManager.apk -> /system/app/WAPPushManager.apk

�ı�����
# �鿴�ļ�����
adb shell cat <file>
# �鿴�ļ���ͷ10��
adb shell head -n 10 <file>
# �鿴�ļ���β10��
adb shell tail -n 10 <file>
root Ȩ�޲���
�˲�����Ҫ root ����ֻ��ſ���ִ��
# ���Կ���rootȨ�ޣ�adb���ӻ����� �ɹ�����ʾ restarting adbd as root
adb root
# �ر�rootȨ��
adb unroot
# ���¹���ϵͳ����,ʹϵͳ�������¿�д �ɹ���ʾ remount succeeded
adb remount
# �����豸������recovery�����sideloadģʽ����ҪrootȨ��
adb reboot sideload
�����Ϳ��Բ��� Android ϵͳ�ļ�

���Ի����µ� dm-verity ���
���� system ���������

�ر��ڵ��Ի����µ�dm-verity���
adb disable-verity
�����ڵ��Ի����µ�dm-verity���
adb enable-verity
ϵͳ��Ŀ
�豸��Ϣ
# �����豸��Ϣ
adb shell cat /system/build.prop
# ������Ϣ
adb shell cat /system/build.prop | grep ro.product
��������
ADB_TRACE ָ����ӡ������Ϣ����������Ϊ�����б��е�ֵ���ö��Ÿ���

adb��sockets��packets��rwx��usb��sync��sysdeps��transport �� jdwp

ANDROID_SERIAL
ָ��Ҫ���ӵ��豸�����ͨ��-sָ������ñ�����������

ANDROID_LOG_TAGS
��ʹ�� logcat ������£�ֻ����Щ��ǩ�ĵ�����Ϣ�Ż��ӡ

dumpsys

adb shell dumpsys wifi

adb shell dumpsys cpuinfo
���� dump ��ǰ���е����ݰ���

���	����
1	SurfaceFlinger
2	accessibility
3	account
4	activity
5	alarm
6	appwidget
7	audio
8	backup
9	battery
10	batteryinfo
11	bluetooth
12	bluetooth_a2dp
13	clipboard
14	connectivity
15	content
16	cpuinfo
17	device_policy
18	devicestoragemonitor
19	diskstats
20	dropbox
21	entropy
22	ethernet
23	hardware
24	input_method
25	iphonesubinfo
26	isms
27	keybar
28	location
29	media.audio_flinger
30	media.audio_policy
31	media.camera
32	media.player
33	meminfo
34	mount
35	netsta
�豸��Ϣ
# �鿴�豸cpu���ڴ�ռ�����
adb shell top
# �鿴ռ���ڴ�ǰ6��app
adb shell top -m 6
# ˢ��һ���ڴ���Ϣ��Ȼ�󷵻�
adb shell top -n 1
# MAC��ַ
adb shell cat /sys/class/net/wlan0/address
# CPU���к�
adb shell cat /proc/cpuinfo
����
# ���豸�����ݹ鵵д���ļ���
adb backup
adb backup -f backup.ab -all
-f ���û�������ʶ�����ݽ���д�뵽��ǰĿ¼�е� backup.ab �ļ���
-apk|-noapk ���� | ���ñ���. apk �ļ��Լ���Ĭ���� noapk
-obb|-noobb ���� | ���ñ���Ӧ�ù����� apk ��չ��Ĭ���� noobb
-shared|-noshared ���� | ���ñ����豸����洢 / SD �е����ݣ�Ĭ���� noshared
-all �������а�װ��Ӧ��
-system|-nosystem ���� - all �Ƿ����ϵͳӦ�ã�Ĭ���ǰ���ϵͳӦ��
packages... ��Ҫ���ݵ�Ӧ���б���������� - all �� - shared ��ʶ����ô����������ǿ�ѡ��
�ӹ鵵�ı����ļ��лָ��豸����

adb restore
adb restore backup.ab
�豸����
# ��������Ӧ�ð����ڴ��󱨸��е��豸��Ϣ
adb bugreport
# ����
adb reboot
# ����ˢ��ģʽ
adb reboot bootloader
# �������ָ�ģʽ
adb reboot recovery
