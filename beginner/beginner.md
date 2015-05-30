# Hướng dẫn cho người mới dùng Ubuntu #

*Lưu ý: Tài liệu này đã cũ và chỉ nhằm mục đích tham khảo*

Tài liệu này dành cho những người muốn bắt đầu dùng Ubuntu, hướng dẫn một cách cơ bản để bạn có thể cài đặt và làm quen với Ubuntu nhanh chóng và dễ dàng.
Mục lục [ẩn]

    1 Giới thiệu về Ubuntu
    2 Cài đặt Ubuntu
        2.1 Những khâu chuẩn bị
            2.1.1 Nhận diện phần cứng
            2.1.2 Lựa chọn phiên bản cài đặt
            2.1.3 Chuẩn bị tập tin cài đặt Ubuntu
                2.1.3.1 Tải Ubuntu
                2.1.3.2 Kiểm tra tập tin cài đặt Ubuntu
            2.1.4 Sơ lược về các cách cài đặt
            2.1.5 Phân vùng ổ cứng
                2.1.5.1 Vài điều cần biết
                2.1.5.2 Hướng dẫn phân vùng ổ cứng
                    2.1.5.2.1 Sơ lược về Hệ thống tập tin (File System hay fs) của Ubuntu
                    2.1.5.2.2 Sử dụng GParted
        2.2 Cài đặt
            2.2.1 Cài đặt bằng đĩa quang (CD/DVD)
            2.2.2 Cài đặt bằng USB boot
                2.2.2.1 Chuẩn bị
                2.2.2.2 Tạo ổ Ubuntu Live USB flash disk
                2.2.2.3 Cài đặt Ubuntu lên đĩa cứng
            2.2.3 Cài đặt bằng files iso từ ổ cứng qua GRUB4DOS
                2.2.3.1 Ưu điểm
                2.2.3.2 Nhược điểm
                2.2.3.3 Cách thực hiện
            2.2.4 Cài đặt bằng Wubi
                2.2.4.1 Chuẩn bị
                2.2.4.2 Tiến hành
            2.2.5 Các cách cài đặt khác
                2.2.5.1 Cài đặt bằng alternateCD
                2.2.5.2 Cài đặt cho những phiên bản cũ hơn
        2.3 Những rắc rối thường gặp
    3 Sử dụng Ubuntu cơ bản
        3.1 Terminal
            3.1.1 Khởi độngTerminal
        3.2 Các tập lệnh
            3.2.1 sudo
            3.2.2 Một số lệnh cơ bản
        3.3 Ubuntu Software Center
        3.4 Synaptics Package Manager và Software Sources
            3.4.1 Synaptics Package Manager
            3.4.2 Software Sources
        3.5 Làm cho Ubuntu hoàn hảo hơn
    4 Những câu hỏi thường gặp
    5 Tài liệu tham khảo

Giới thiệu về Ubuntu

Hệ điều hành là phần thiết yếu nhất của hệ thống phần mềm trên một hệ thống máy tính. Hệ điều hành là một bộ các phần mềm chịu trách nhiệm quản lý tài nguyên phần cứng và cung cấp các dịch vụ ở mức cơ bản cho các phần mềm khác để chúng có thể hoạt động và thực hiện chức năng. Nhân là một bộ phận cấu tạo nên hệ điều hành, chịu trách nhiệm quản lý phần cứng ở mức sâu nhất, chạy các tiến trình, v.v...
Cài đặt Ubuntu
Những khâu chuẩn bị
Nhận diện phần cứng

Công đoạn này nhằm mục đích xác định những thông tin cơ bản về hệ thống mà bạn định cài đặt Ubuntu, nhằm lường trước những khó khăn sẽ gặp phải, đồng thời cũng tiện cho bạn report lỗi sau này trong quá trình sử dụng.

Để lấy thông tin về phần cứng hệ thống cài đặt có nhiều cách, sau đây sẽ giới thiệu một cách đơn giản nhất là sử dụng LiveCD Ubuntu.

Các bạn cho đĩa Ubuntu vào ổ CD/DVD (hoặc boot bằng USB, GRUB4DOS tùy vào khả năng), sau đó bạn chọn Try Ubuntu (LiveCD).

Với các phiên bản 10.04, 10.10, các bạn vào Applications (Ứng dụng)  => Accessories (Công cụ) => Terminal (hoặc Thiết bị cuối)

Với các phiên bản 11.04, 11.10 và những phiên bản mới hơn dùng Unity, các bạn nhấn phím Super (phím Windows) rồi gõ Terminal, sau đó chọn Terminal ở phía dưới

Các bạn gõ lspci để kiểm tra các thiết bị mà Ubuntu đã nhận:

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]

lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc RV730XT [Radeon HD 4670]

lspci | grep Ethernet
02:00.0 Ethernet controller: Attansic Technology Corp.L1 Gigabit Ethernet Adapter (rev b0)

lspci | grep Network
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

Trong đoạn minh họa ở trên, phần đầu tiên ta quan tâm tới là các thiết bị âm thanh, tiếp sau là VGA và Card Ethernet, Card Wifi (nếu có).Nếu máy bạn hiển thị đủ những mục này thì coi như Ubuntu đã nhận đầy đủ Drivers.

Một cách trực quan nhất để biết máy bạn có chạy Ubuntu tốt hay không là bạn có thể kiểm tra mọi thứ khi chạy LiveCD, nếu mọi thứ đều ổn: Âm thanh tốt, màn hình hiển thị ok, truy cập mạng bình thường bằng dây hoặc Wifi...
Lựa chọn phiên bản cài đặt

Mỗi bản Ubuntu khi ra đời đều mang theo những triết lý mà những nhà phát triển gửi gắm theo nó.

Ubuntu thường release các phiên bản mới vào cuối tháng 4 và đầu tháng 10 của mỗi năm. Mỗi phiên bản thường sẽ được hỗ trợ 18 tháng, những phiên bản có gắn nhãn LTS (Long Term Support) sẽ được hỗ trợ lâu hơn : 3 năm với phiên bản desktop và 5 năm cho phiên bản Server. Những bản gắn nhãn LTS thường ổn định hơn và cũng được chăm chút nhiều hơn những phiên bản thường, nói chung chúng là những phiên bản ổn định và có tính đột phá.

Mỗi lần ra phiên bản mới Canonical  đưa ra một loạt các phiên bản phục vụ cho nhiều hệ máy, cũng như là sở thích người dùng:

    Ubuntu : sử dụng môi trường đồ họa GNOME (phiên bản 2 (Ubuntu 10.04, 10.10 và 11.04) hoặc phiên bản 3 (11.10 và các phiên bản mới hơn)) hoặc Unity (Ubuntu 11.04 và 11.10). GNOME 2, GNOME 3 và Unity đều là những giao diện đẹp, dễ sử dụng cho những người mới dùng, tích hợp hiệu ứng Compiz 3D đẹp mắt.
    Kubuntu : sử dụng môi trường đồ họa KDE, một môi trường đẹp và hào nhoáng, theo đánh giá của nhiều người dùng là có vẻ khó sử dụng hơn giao diện của Ubuntu và yêu cầu cấu hình cao hơn.
    Xubuntu : sử dụng giao diện Xfce là một giao diện đồ họa, đơn giản , dễ dàng và nhẹ nhàng. Vì thế Xubuntu thích hợp cho những dòng máy cấu hình thấp và những ai yêu sự đơn giản.
    Lubuntu : sử dụng giao diện LXDE, một môi trường lightweight cực kì nhẹ, sử dụng cho những máy quá yếu, tuy nhiên Lubuntu không được đánh giá cao lắm.
    Ubuntu Netbook Edition : tương tự như phiên bản Desktop thông thường nhưng được tùy chỉnh những giao diện phù hợp cho máy netbook (các bạn vẫn có thể chuyển đổi từ bản Desktop -> Netbook khi cài xong). Hiện tại (2012) thì phiên bản Netbook đã được tích hợp vào phiên bản Desktop của Ubuntu.
    Ubuntu Server Edition : Phiên bản dành cho máy chủ, không có giao diện đồ họa mặc định khi cài đặt.

Ngoài những phiên bản chính được Canonical Release, còn khá nhiều các phiên bản Remix khác không phải của Canonical như : Mythubuntu, Ubuntu-Studio, Ubuntu Games, .v.v.
Cấu hình tối thiểu và khuyên dùng Phiên bản
	Tối thiếu
	Khuyên dùng
Ubuntu Desktop Edition
	

CPU : 700 MHz x86

RAM : 384 MB

HDD : 3 - 5 GB
	

CPU : 1GHz

RAM : 1GB

HDD : 15GB
Ubuntu Desktop (GUI) Installation 	

CPU : 1GHz x86

RAM : 512 MB

HDD : 5GB
	
Ubuntu Netbook Edition
	

CPU : Intel Atom@1.6GHz

RAM : 512MB

HDD : 5GB
	
Kubuntu 	

CPU : 700 MHz x86

RAM : 384 MB

HDD : 8G
	
Xubuntu
	

RAM : 256MB

HDD : 2GB
	


Tùy thuộc vào nhu cầu và cấu hình máy mà bạn có thể lựa chọn phiên bản cài đặt cho phù hợp với mình.

Trên đây chỉ là những cấu hình tham khảo khi muốn cài đặt Ubuntu, với những phiên bản hiện tại thì cầu hình có thể cao hơn (RAM, CPU) vì thế nếu máy của bạn yếu thì bạn có thể sử dụng những phiên bản Xubuntu hay Lubuntu hoặc Debian với giao diện xfce hoặc lxde cùng các ứng dụng lightweight khác.


Chuẩn bị tập tin cài đặt Ubuntu
Tải Ubuntu

Ubuntu có nhiều loại đĩa cài đặt, phục vụ như cầu của nhiều cách cài đặt khác nhau, người dùng khác nhau, cũng như các điều kiện khác như : Internet, sở thích, .v.v.

    Live CD: giúp bạn chạy Ubuntu từ đĩa khởi động mà không cần cài đặt bất cứ thứ gì lên ổ cứng. Thích hợp nếu để bạn thử nghiệm Ubuntu có chạy tốt với hệ thống của bạn hay không.
    Alternate: đĩa cài đặt ở chế độ text-mode (giống như đĩa cài đặt Windows XP), không có giao diện đồ họa, nhanh hơn LiveCD và có thể dùng để nâng cấp hệ thống lên phiên bản cao hơn. Đồng thời, phiên bản này cũng cho phép bạn lựa chọn các gói cài đặt tùy vào nhu cầu của bạn sử dụng. Đĩa này thường được sử dụng để cài cho những máy cấu hình yếu hoặc có lỗi phát sih không chạy LiveCD được.
    DVD: tương tự như LiveCD nhưng chứa nhiều gói phần mềm hơn, thích hợp cho các bạn không có điều kiện Internet tốt. Phiên bản DVD cài chậm hơn nhiều so với phiên bản CD nên bạn có thể dùng CD để cài đặt và DVD để cài phần mềm. 

Các tệp ISO của Ubuntu, Kubuntu, Xubuntu thường có dạng :

{*ubuntu}-{phiên bản}-{desktop|alternate|DVD}-{arch}.iso

    {*ubuntu} : ubuntu, kubuntu hoặc xubuntu
    {phiên bản} là tên mã của phiên bản Ubuntu. Ví dụ : 10.04, 9.10, .v.v.
    {desktop|alternate|DVD} : loại đĩa desktop (LiveCD), alternate (Alternate), DVD (DVD)
    {arch} : phiên bản 32bit (i386) hoặc 64bit (amd64) [ amd64 chỉ là kí hiệu của hệ 64bit, chip Intel hay AMD chỉ cần hỗ trợ 64bit đều cài được] 

Ví dụ : ubuntu-10.04-desktop-i386.iso : Live CD Ubuntu phiên bản 10.04 cho máy 32bit

Các bạn có thể Download Ubuntu tại trang web chính thức của Ubuntu : http://www.ubuntu.com/desktop/get-ubuntu/download

Mặc định đây sẽ là bản LiveCD, các bạn có thể nhấn vào http://www.ubuntu.com/desktop/get-ubuntu/alternative-download để tải những phiên bản khác.

Chú ý :

    Khi ta chọn Download bằng trang Web chính thức của Ubuntu, Ubuntu sẽ tự chọn 1 Server cho ta download, tuy nhiên tốc độ nhanh chậm thì rất may rủi. Vì thế, lời khuyên cho các bạn là chọn 1 server ở Việt Nam (hoặc gần Việt Nam như China, Taiwan, Singapore .v.v.). Hiện tại ở Việt Nam, có 2 mirror chính của Ubuntu là Virror ( do HaNoiLUG lập ra, tốc độ nhanh, cập nhật tốt ) và FPT ( tốc độ rất nhanh với những bạn dùng mạng FPT, và những mạng khác thì cũng tương đối, tuy nhiên mirror này rất thiếu ổn định, hay *ngáp ngoải* ).
    Bạn nên dùng những trình hỗ trợ Download để tải Ubuntu vì file cài đặt khá lớn, nếu tải bình thường rất dễ gây hỏng file trong quá trình tải. Một vài trình hỗ trợ download tốt và miễn phí : Orbit Downloader, Flashget, DownThemAll [ Addons của Firefox]
    Nếu có đường truyền tốt, bạn có thể sử dụng phương pháp tải bằng Torrent, phương pháp tải này cũng rất nhanh và ít gây lỗi trong quá trình tải.
    Nếu không có điều kiện đường truyền Internet, bạn có thể mua CD từ các của hàng tin học hoặc tại đây, hoặc Yêu cầu đĩa miễn phí từ Canonical hoặc yêu cầu để được hỗ trợ thêm từ những thành viên nhiệt thành của cộng đồng Ubuntu Việt Nam 

Kiểm tra tập tin cài đặt Ubuntu

Do nhiều lý do, trong quá trình tải về file cài đặt của Ubuntu thường bị hỏng, để kiểm tra xem file cài đặt có bị hỏng hay không, bạn có thể dựa vào việc checksum MD5 hoặc SHA

Tham khảo chi tiết về MD5 và cách checksum MD5 ở đây

Mã MD5 dùng để checksum bạn có thể lấy ở đây : releases.ubuntu.com/10.04/MD5SUMS thay bằng phiên bản khác nếu bạn muốn checksum cho phiên bản khác bản 10.04

Hoặc có thể lấy số checksum trực tiếp ở đây :

0b0e0d36050d9980ec995262eb9f2e6b *ubuntu-10.04-netbook-armel+dove.img
9e0d6ac7b69bb7912d49369a6807e39d *ubuntu-10.04-netbook-armel+imx51.img
712277c7868ab374c4d3c73cff1d95cb *ubuntu-10.04-netbook-i386.iso
f3da7da6931e3160738b3067d79e346a *ubuntu-10.04.1-alternate-amd64.iso
1c77abb717e7c1ad28611fd81510c758 *ubuntu-10.04.1-alternate-i386.iso
b4faa186c2419dc26e522e5f82e268a1 *ubuntu-10.04.1-desktop-amd64.iso
9a95ed6f6ec38fb58c446dba1add6a08 *ubuntu-10.04.1-desktop-i386.iso
142aaaa77e7da94ae62d7ee2f39d8b3b *ubuntu-10.04.1-server-amd64.iso
01f72c846845e4e19aec8a45912e5dda *ubuntu-10.04.1-server-i386.iso
5c976b1d655b10df3b10811e77b09a25 *wubi.exe

Sơ lược về các cách cài đặt

Để cài đặt Ubuntu có rất nhiều cách, mục này giới thiệu sơ lược với bạn các cách cài đặt Ubuntu, để bạn phần nào đó có cái nhìn tổng quan và lựa chọn cách cài đặt phù hợp với mình.

    Cài đặt chuẩn từ CD/DVD : Đây là cách cài đặt cổ điển nhất, với ưu điểm là quen thuộc. Tuy nhiên do dung lượng đĩa cài Ubuntu khá lớn, trong khi đĩa CD của chúng ta chất lượng lại không đảm bảo nên cách này thường xảy ra lỗi trong những phiên bản gần đây. Tuy nhiên, đa phần các trường hợp vẫn cài đặt thành công.
    Cài đặt từ USB Flash Disk : Một cách cài đặt rất tiện dụng vì USB Flash Disk hiện nay là một thiết bị quá quen thuộc với mọi người. Ưu điểm là nhanh (thường chỉ mất khoảng 15 phút để cài đặt xong so với CD là khoảng 30~45 phút), việc cài đặt hầu như ít xảy ra lỗi. Nhược điểm của phương pháp này là bạn cần có USB Flash Disk, và bo mạch chủ (mainboard) phải hỗ trợ khởi động từ USB (đa số bo mạch chủ hiện nay đều hỗ trợ).
    Cài đặt thông qua GRUB4DOS bằng tập tin ISO : Nhanh như cách cài bằng USB, không cần chép ra CD, không cần tạo USB boot, tuy nhiên yêu cầu bạn có một chút kĩ năng và không phải lúc nào cũng thành công trên mọi hệ máy.
    Cài đặt bằng Wubi : Ưu điểm là bạn không cần phải có quá nhiều kinh nghiệm, Wubi sẽ giúp bạn hoàn thành tất cả, đặc biệt bạn không cần phải động gì đến ổ cứng (an toàn tuyệt đối cho dữ liệu), cài đặt - gỡ bỏ chỉ đơn giản như một phần mềm Windows bình thường, tuy nhiên cách cài đặt này không phải lúc nào cũng thành công lúc cài đặt và cũng khó để giải quyết. Thêm vào đó, cài qua Wubi sẽ gặp phải một số rắc rối về Bootloader và tốc độ chậm hơn cài thẳng vào ổ cứng. Tất nhiên, nếu bạn muốn thử cảm giác với Ubuntu và ngại cài đặt thì đây là một lựa chọn thích hợp. 

Phân vùng ổ cứng

Sau khi nhận diện cơ bản về phần cứng cài đặt, chúng ta bắt đầu quá trình chuẩn bị phân vùng cho việc cài đặt.
Vài điều cần biết

Vì sao chúng ta phải phân vùng ổ cứng? Và phân vùng ổ cứng là gì?

Phần vùng ổ cứng tức là chúng ta làm công việc chia ổ cứng thành các "phần" khác nhau (ổ C, D , E, ... với Windows và /dev/sda1, /dev/sda2, ... với Linux). Và việc làm này rất có lợi cho máy và cho chúng ta. Với việc chia ổ cứng thành những "phần" nhỏ hơn sẽ giúp cho máy và chúng ta sắp xếp các file một cách dễ dàng, dễ quản lý và tìm kiếm hơn, tức sẽ làm cho tốc độ truy cập dữ liệu sẽ nhanh hơn rất nhiều. Và điều đặc biệt là, khi một trong những "phần" nhỏ bị hỏng, thì chỉ những file trong "phần" đó đó mới bị ảnh hưởng, còn những "phần" khác không bị sao cả!

Việc phân vùng có phải đơn giản chỉ là chia nhỏ thành các "phần" không?

Đúng là như thế! Nhưng chúng ta không dừng ở đó, mà mỗi phân vùng nhỏ phải được định dạng nhất định!

Thông thường người ta thường dùng những định dạng sau:

    FAT32: đây là định dạng hệ thống tập tin của Window, đây là một định dạng cũ, được Window sử dụng từ phiên bản Window 95.Nên hiện tại nó có rất nhiều hạn chế, đặc biệt là bạn không thể để 1 file dung lượng quá 4Gb vào phân vùng định dạng FAT32 mặc dù phân vùng đó còn thừa hơn 4Gb. 

    NTFS: đây cũng là định dạng hệ thống tập tin của Window.Được window chọn làm định dạng tiêu chuẩn từ phiên bản Window 2000 cho tới Window 7 hiện nay.Định dạng này có nhiều ưu điển hơn FAT32 rất nhiều, đặc biệt là nó có thể lưu trữ được những file có dung lượng lớn hơn 4Gb, và tốc độ truy cập, xử lý, làm việc với file cũng nhanh hơn rất nhiều so với FAT32. 

    EXT3: đây là định dạng hệ thống tệp tin của linux. Hiện tại, định dạng này được những người sử dụng linux ưa chuộng dùng. 

    EXT4: đây là một định dạng mới, được Ubuntu hỗ trợ từ phiên bản 9.04. Hiện nay, EXT4 đã ổn định, mọi người được khuyên dùng định dạng này cho việc cài đặt Ubuntu.

    Swap: đây là một định dạng được Ubuntu sử dụng với mục đích làm ổ để dữ liệu tạm thời trong quá trình làm việc, dùng cho việc "ngủ đông* (Hibernate), không dùng trong việc lưu trữ dữ liệu của người dùng. Với mỗi hệ điều hành Ubuntu đều yêu cầu có một ổ Swap. Với nhu cầu sử dụng thông thường với những hệ thống RAM > 4GB thì swap hầu như ít được hệ thống sử dụng tới, nhưng chúng tôi khuyên bạn nên có 1 phân vùng swap tối thiểu khoảng 512MB và đúng tiêu chuẩn là dung lượng bằng 2 lần RAM của hệ thống. Ví dụ bạn dùng 512MB RAM thì swap bạn sẽ để 1GB.

Hướng dẫn phân vùng ổ cứng

    Bước 1: Bạn cần phải xác định rõ ổ cứng của mình có tổng dung lượng là bao nhiêu, hiên tại đã có phân vùng nào chưa (đối với ổ cứng cũ), và bạn định chia lại ổ như thế nào, mỗi phân vùng được dùng vào việc gì và dung lượng cho mỗi phân vùng là bao nhiêu.
    Bước 2: Tiến hành công việc phân vùng 

         Lưu ý : để tránh việc bị mất dữ liệu, làm hỏng ổ cứng, yêu cầu bạn đọc tuân thủ, thực hiện nghiêm túc các quy tắc sau

    Chỉ tiến hành phân vùng ổ cứng lúc điện ổn định, khi điện chập chờn hoặc có nguy cơ bị mất điện thì tuyệt đối không làm.
    Chỉ tiến hành khi đã vững lý thuyết, nắm được các bước, thao tác thực hiện.
    Trong quá trình làm, các thao tác làm phải từ từ, chính xác, dứt khoát, chú ý tuyệt đối.
    Sau khi thực hiện một thao tác nào đó mà thấy máy có biểu hiện bị đơ hoặc chưa có phản ứng gì, xin vui lòng kiên nhẫn chờ đợi.
    Nghiêm cấm kích bừa bãi, kích nhiều lần vào các nút trong cửa sổ phân vùng, sau khi kích xong chờ máy làm xong thao tác đó mới bắt đầu chuyển sang thao tác khác.
    Tuyệt đối không khởi động lại máy trong quá trình đang phân vùng.
    Nhưng khi phát hiện mình xóa, fomat, định dạng nhầm ổ, thì lập tức tắt máy( có thể ngắt luôn nguồn điện) nếu thao tác dừng không có hiệu quả, sau đó nên nhờ người có kinh nhiệm trong việc cứu dữ liệu để khắc phục tình trạng này, hoặc có thể tự mình cứu dữ liệu nhờ các công cụ cứu dữ liệu. Chú ý rằng phân vùng đã bị fomat trên 1 lần hoặc đã ghi đè dữ liệu lên thì khả năng lấy lại dữ liệu đã mất là cực thấp. 


Sơ lược về Hệ thống tập tin (File System hay fs) của Ubuntu

Ubuntu không có khái niệm ổ C, D, E .v.v. như Windows, thay vào đó hệ thống Ubuntu chỉ có một phân vùng là root ( / ) và các mount point để mount (gắn) các phân vùng khác vào.

Ví dụ : phân vùng DATA có thể được gắn vào /media/DATA.

Ubuntu gọi tên các ổ cứng bằng /dev/sda (sdb) (hoặc hda, hdb, .v.v.) và tên cái phân vùng là /dev/sda1, /dev/sda2 (hda1, hda2 ...) thay cho chữ cái C, D, E như Windows.

Ubuntu nói riêng và Linux nói chung cần tối thiểu khoảng 2 phân vùng để có thể cài đặt.

+ Phân vùng root (/) : Chứa tất cả các thành phần của hệ thống bao gồm cả những mount point dùng để mount những phân vùng khác. Ubuntu yêu cầu tối thiểu 4.6G, chúng tôi khuyên dùng 10~15GB

+ Phân vùng swap : Dùng để hệ thống khi thiếu RAM, dữ liệu sẽ được tự nạp lên phân vùng này để xử lý. Nếu RAM > 4GB, mặc dù swap lúc đó rất ít được sử dụng nhưng vẫn nên có phân vùng Swap khoảng 512MB chẳng hạn, nhưng chúng tôi khuyên nếu bạn không quá hạn hẹp về ổ cứng thì nên để Swap có dung lượng bằng 2 lần RAM hệ thống. Ví dụ bạn dùng RAM 512MB thì phân vùng Swap khuyến cáo nên dùng là 1GB

Sau đây sẽ là 2 cách phân vùng khuyên dùng : sử dụng GParted (có ngay trong LiveCD) và Acronis Disk Director Suite.
Sử dụng GParted

Đầu tiên bạn khởi động bằng LiveCD của Ubuntu. Khi cài đặt Ubuntu bạn có thể chọn Guide để Ubuntu tự xử (chạy ngon). Hoặc bạn có thể tự làm chủ việc phân vùng bằng cách chọn Manual nếu không yên tâm vào Ubuntu. Không hiểu sao lúc phân vùng khi cài đặt Ubuntu lại không có chuyện Extended, Logical, Primary nên mình khuyên các bạn nên phân vùng trước khi cài đặt bằng GParted (có sẵn trong đĩa Ubuntu). Các bạn nên đọc hết 1 lần bài hướng dẫn này rồi mới thực hiện để có thể tạo ra những phân vùng phù hợp với nhu cầu của mình.

GParted (Partition Editor)

Các phân vùng được đánh số theo thứ tự hda1 đến hda9. Trong hình minh họa hda1 là phân vùng NTFS (Primary) , hda2 (Extended), hda3 và hda4 là phân vùng ext3 (Primary). hda5->hda9 đều là phân vùng Logical.

Với 1 phân vùng chứa dữ liệu bạn có thể thay đổi kích thước (resize) nó lại mà vẫn đảm bảo an toàn cho dữ liệu của mình. Các thay đổi trên phân vùng của bạn chỉ thực hiện sau khi bạn bấm Apply vì vậy cứ thoải mái thay đổi cho hợp với ý thích của mình.

Huong dan phan vung-h2.jpg

Free Space Followinglà dung lượng phân vùng phía sau khi đã thay đổi kích thước của phân vùng có sẵn. Sau khi Resize vùng mới phía sau sẽ có dạng (Unallocate)

Bạn cũng có thể delete một phân vùng có sẵn để tạo một phân vùng mới lúc đó phân vùng mới cũng ở dạng Unallocate. Trong ví dụ mình delete phân vùng hda4.

Huong dan phan vung-h3.jpg

Sau đó bạn có thể định dạng cho phân vùng của bạn. Bằng cách chọn Create new partition ở phân vùng Unallocated.

Huong dan phan vung-h4.jpg

Sau khi đã tạo được các phân vùng để cài đặt ( 1 phân vùng cho thư mục gốc / và một phân vùng cho Swap (có hay không cũng được)) bạn nhấn vào Apply để thực hiện các thao tác phân vùng.

Tiếp theo mình chọn một phân vùng để làm SWAP. (Kích thước theo lời khuyên của mọi người là = 2 lần số RAM của bạn có. Nhưng với máy của mình RAM nhiều nên cũng thường bỏ qua không tạo phân vùng SWAP). Nhiệm vụ của phân vùng SWAP dùng để thay thế RAM để tăng tốc máy khi máy gần hết RAM.

Huong dan phan vung-h6.jpg
Cài đặt
Cài đặt bằng đĩa quang (CD/DVD)

Video hướng dẫn cài đặt Ubuntu bằng đĩa CD có tại YouTube

Sau khi cài đặt Ubuntu xong, bạn chuyển đến tiếp phần Sử dụng Ubuntu cơ bản
Cài đặt bằng USB boot
Chuẩn bị

Chuẩn bị cơ bản
Cũng như cài đặt hệ điều hành bằng các cách khác, đầu tiên bạn cũng cần phải có những chuẩn bị cho việc cài đặt: phân vùng ổ cứng làm nơi cài đặt, kiểm tra tương thích phần cứng mà lựa chọn phiên bản thích hợp, ....


Tải chương trình hỗ trợ
Để tiến hành cài đặt Ubuntu cũng như nhiều phiên bản khác từ ổ nhớ di động USB Flash, bạn cần có chương trình hỗ trợ tạo ổ USB Flash khởi động, điển hình là chương trình UNetbootin (Universal Netboot Installer).Bạn có thể vào trang web unetbootin.sourceforge.net để tải về bản mới nhất của phần mềm này.Ở đây bạn có thể tìm thấy cả 2 phiên bản cho phép chạy trên Windows và Linux.
Tạo ổ Ubuntu Live USB flash disk

Có rất nhiều công cụ hỗ trợ việc này như Unetbootin, Universal USB Installer, ...

Kích hoạt chương trình UNetbootin
UNetbootin là chương trình chạy không cần cài đặt.Với Windows bạn chỉ việc click đúp vào tệp thực thi (.exe) vừa tải về là có thể sử dụng được luôn.Với Linux cũng như vậy, điểm chú ý là bạn có thể phải thêm thuộc tính thực thi cho tệp vửa tải về để có thể chạy được nó, ngoài ra Unetbootin cần thêm các gói mtools để làm việc với USB drive, p7zip-full để giải nén dữ liệu từ tệp tin iso.

Giao diện UNetbootin
Cả 2 phiên bản chương trình UNetBootin cho Windows và Linux đều có giao diện đồ họa trực quan và  dễ dàng sử dụng.
Unetbootin Screenshot 1 on Windows XP

Cửa sổ chính của UNetbootin như trên có thể chia làm 2 phần chính: phần trên gồm các lựa chọn nguồn dữ liệu để tạo ổ USB flash khởi động, phần dưới là phần chọn thiết bị làm vị trí cài đặt.
UNetbootin có 3 lựa chọn nguồn dữ liệu để tạo ổ USB flash khởi động.

    Distribution: tự động tải tệp iso từ server về và tiến hành cài đặt.Bạn có thể chọn dòng Linux cũng như phiên bản của dòng đó ở 2 ô bên cạnh.UNetbootin hỗ trợ hầu hết các dòng Linux thông dụng hiện nay.Phiên bản của từng dòng mà nó hỗ trợ là phiên bản mới nhất trở vể trước tính từ lúc phiên bản UNetbootin bạn đang dùng ra đời.Như vậy sau mỗi lần một dòng Linux cho ra đời 1 phiên bản mới UNetbootin cũng phải ra một phiên bản mới để cập nhật lại sự thay đổi này.Để xem phiên bản Linux mà UNetbootin hỗ trợ, bạn có thể xem tại nơi tải phần mềm này đã giới thiệu ở trên.

    Diskimage: cài đặt từ một tệp sao lưu nào đó.UNetbootin cho phép 2 kiểu dữ liệu sao lưu là tệp iso và tệp sao lưu đĩa mềm.Tệp sao lưu đĩa mềm hiển nhiên là chỉ cho phép khởi động máy tính mà thôi nên ta không xét đến.Hãy chọn kiểu tệp ISO và chọn đến tệp iso của đĩa cài đặt Ubuntu mà bạn đã tải về từ Internet hay copy ở đâu đó.

    Custom: cài đặt tùy chọn.Phần này cần có những hiểu biết về quá trình khởi động của máy tính nên ta không tìm hiểu phần này.

UNetbootin không chỉ cho phép tạo các ổ USB Flash khởi động làm đĩa cài đặt cho Linux mà còn có thể chép đĩa cài đặt lên ổ cứng và cho phép bạn cài Linux từ ổ cứng.Bạn có thể chọn kiểu ổ lưu trữ là USB drive hoặc Hard drive, hoặc chọn Show all Drives để hiển thị tất cả các thiết bị liên kết đến máy tính của bạn (nếu chọn phần này cần chú ý khi chọn là có những thiết bị trong danh sách không phải thiết bị lưu trữ nên không cài đặt được).Sau đó bạn có thể chọn thiết bị làm vị trí cài đặt
Hãy lựa chọn theo ý muốn của bạn để có thể tạo được một ổ Ubuntu Live USB flash disk.Và bây giờ bạn có thể nhấn OK để tiếp tục.

Tiến trình thực hiện
Sau khi bạn nhấn OK, việc tiếp theo là ngồi chờ mà thôi.UNetbootin sẽ tạo các tệp tin khởi động lên ổ USB Flash (hoặc ổ cứng tùy theo bạn đã chọn, và nếu bạn chọn ổ cứng thì nó sẽ thêm vào menu khởi động một mục cho phép bạn khởi động máy tính từ đĩa cài đặt Ubuntu như một hệ điều hành trên ổ cứng) và giải nén dữ liệu từ tệp tin iso vào ổ USB flash (hoặc vào ổ cứng).Tốc độ nhanh hay chậm tùy thuộc vào cấu hình máy.
Unetbootin screenshot 2 on Win


Và bây giờ bạn đã có trong tay một Ubuntu Live USB flash disk (hoặc Ubuntu Live Hard disk).

Bây giờ ta chuyển sang giai đoạn cài đặt Ubuntu.
Cài đặt Ubuntu lên đĩa cứng

Bạn hãy khởi động lại máy tính để xem thành quả công việc của mình.

    Nếu bạn đã tạo 1 Ubuntu Live USB flash disk thì phải đảm bảo ổ USB flash đã kết nối vào máy tính trước khi bật máy.Vào BIOS setup chỉnh First boot device là USB (USB-HD).Cần lưu ý là một số mainboard coi ổ USB flash tương đương với ổ cứng nhưng có độ ưu tiên thấp hơn, để khởi động được từ ổ USB flash bạn cần vào phần Hard disk boot priority (hay tương tự) chỉnh ổ USB flash lên trên (vì ổ USB flash là di động nên thứ tự này không được lưu lại cho lần boot sau.Vì thế lần boot sau bạn vẫn phải vào đây để chỉnh lại thứ tự ưu tiên để có thể boot từ ổ USB flash).

    Nếu bạn đã tạo Ubuntu Live USB Hard disk thì khi khởi động trên menu boot sẽ có thêm một mục cho phép bạn khởi động máy tính như là khởi động từ đĩa Live CD.

Và bây giờ bạn đã khởi động được Live Ubuntu.Công việc tiếp theo là cài đặt ubuntu tương tự hướng dẫn Cài đặt từ CD/DVD
Cài đặt bằng files iso từ ổ cứng qua GRUB4DOS

Phương pháp này áp dụng khi bạn không muốn (hoặc không có điều kiện) dùng USB, CD/DVD.
Ưu điểm

    Nhanh (vì boot trực tiếp từ files ISO trên ổ cứng)

    Không tốn CD, không mất công Burn hoặc tạo USB Boot (chưa kể một số mainboard không có chức năng boot từ USB)

Nhược điểm

    Kĩ thuật phức tạp hơn những cách cài khác.

Cách thực hiện

1.Chuẩn bị những thứ cần thiết

Đầu tiên, bạn tải GRUB4DOS phiên bản mới nhất từ SourceForge về.Sau đó, giải nén, copy grldr.mbr và grldr vào ổ đĩa hệ thống của Windows (mặc định là ổ C ).

Tiếp đó, copy file ISO Ubuntu vào ổ C.

2.Thiết lập BootLoader

Với Windows XP, các bạn mở file C:\boot.ini ra và thêm dòng sau vào trong boot.ini

C:\grldr="Start GRUB4DOS"

Với Windows Vista, Windows 7, các bạn mở cmd với quyền Administrator, và chạy lần lượt các lệnh :

   bcdedit /create /d "Start GRUB4DOS" /application bootsector
   bcdedit /set {id} device boot
   bcdedit /set {id} path \grldr.mbr
   bcdedit /displayorder {id} /addlast

Với {id} ở đây là cái mà khi bạn chạy lệnh đầu tiên nó hiện ra.

3.Tạo menu.lst

Bạn dùng một cái Text Editor nào đó, như Notepad, Wordpad chẳng hạn, tạo 1 file với nội dung như sau :

timeout 5

title Install Ubuntu
find --set-root /ubuntu-10.04-desktop-i386.iso
map /ubuntu-10.04-desktop-i386.iso (0xff)
map --hook
root (0xff)
kernel /casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-10.04-desktop-i386.iso quiet splash --
initrd /casper/initrd.lz
boot

Với ubuntu-10.04-desktop-i386.iso là tên file ISO bạn để ở ổ C.

Lưu lại thành tệp menu.lst trong thư mục chủ của ổ C.

4.Boot bằng file ISO và cài đặt.

Trước khi reboot, bạn cần chắc chắn rằng 4 tệp :  grldr.mbr, grldr, menu.lst và file ISO ubuntu đã ở trong ổ C.

Sau khi reboot, đến màn hình chọn, các bạn chọn Start GRUB4DOS, sau đó chọn Install Ubuntu.

Quá trình sau đó diễn ra bình thường như cài đặt bằng CD.
Cài đặt bằng Wubi

Wubi là viết tắt của Windows-based Ubuntu Installer, là một chương trình cho phép bạn cài đặt Ubuntu ngay từ trong Microsoft Windows nhằm giúp bạn dùng Ubuntu mà không phải tạo ra bất kỳ một thay đổi đáng kể nào lên phân vùng đĩa cứng. Wubi có thể được sử dụng với hầu hết tất cả các hệ điều hành Microsoft Windows hiện nay.

Lời khuyên: Nếu bạn có ý định sử dụng Ubuntu một cách lâu dài, hãy cân nhắc đến việc cài đặt Ubuntu xuống đĩa cứng một cách chính thống. Hiệu suất (performance) của Ubuntu chạy Wubi kém hơn so với Ubuntu chạy native trên ổ cứng, nhất là khi ổ cứng của bạn bị phân mảnh. Chức năng Hibernation cũng không hoạt động nếu bạn dùng Ubuntu với Wubi. Độ phân mảnh của phân vùng NTFS và FAT32 của Windows tăng lên rất nhanh theo thời gian, do đó hiệu suất Ubuntu chạy Wubi của các bạn có thể giảm nhanh theo thời gian.
Chuẩn bị

    Wubi: Bạn có thể chạy phiên bản Wubi có sẵn trong đĩa quang Ubuntu hoặc tải về từ trang chủ của Wubi. Bộ cài đặt Wubi chỉ có 1467844 B (~ 1.4 MB) (tính đến ngày 20/08/2010).
    Đường truyền Internet tương đối tốt: Wubi sẽ tải tập tin ISO Ubuntu tương ứng, có dung lượng ~ 600 MB, do đó một đường truyền Internet tốt sẽ rất có ích cho bạn.
    Chỗ trống đĩa cứng: Tối thiểu tầm 4 GB, khuyến cáo sử dụng 8 GB trở lên. Định dạng phân vùng là NTFS. 

Tiến hành

    Chạy Wubi, giao diện bản Wubi (tính đến ngày 20/08/2010) có dạng như sau:

        Giao diện khởi động Wubi

    Các lựa chọn:
        Installation drive: Chọn ổ đĩa cài đặt.
        Language: Chọn ngôn ngữ cài đặt.
        Installation size: Kích thước cài đặt lên đĩa cứng, đây chính là kích thước tối bạn quy định cho toàn bộ hệ điều hành Ubuntu của bạn.
        Username và Password: tên đăng nhập và mật khẩu tương ứng.
        Desktop environment: Môi trường desktop của bạn, mặc định là GNOME (Ubuntu), tuy nhiên bạn có thể chọn một vài tùy chọn khác như KDE (Kubuntu), XFCE (Xubuntu), ... 
    Sau khi lựa chọn xong bạn có thể chọn Accessibility để chọn các tùy chọn nhằm tăng khả năng tương tác với máy (thường dành cho người khuyết tật), nhấn Install để Wubi tiến hành công việc của mình. Máy tính sẽ khởi động lại và bạn sẽ thấy có thêm một mục trong Boot screen:

        Giao diện boot Wubi

    Bạn chọn Ubuntu và tiến hành các bước cài đặt như trong phần: [[1]] 

Các cách cài đặt khác
Cài đặt bằng alternateCD
Cài đặt cho những phiên bản cũ hơn
Những rắc rối thường gặp

Việc cài đặt Ubuntu nói chung là tương đối dễ dàng, tuy nhiên trong quá trình cài đặt vẫn có thể gặp phải một số rắc rối nhỏ, nhưng không đáng lo.
Mục sau sẽ giúp các bạn khắc phục một vài lỗi trong số chúng.


    Boot được từ CD, USB Boot, nhưng khi chọn menu thì không boot được tiếp nữa, hoặc gặp lỗi.

Nguyên nhân của việc này, chủ yếu là do file ISO hoặc đĩa CD của bạn bị lỗi.Điều đó khiến bạn không thể boot được vào LiveCD Ubuntu để thực hiện việc cài đặt.
Để giải quyết việc này .
+ Với file ISO dùng tạo USB Boot (hoặc cài qua ổ cứng), bạn cần checksum MD5 (hoặc SHA1) xem có trùng khớp không, để đảm bảo file ISO không bị lỗi trong quá trình tải.Nếu không khớp, bạn cần tải lại file ISO này.
Tham khảo thêm về MD5 CHECKSUM
Mẹo : nếu có 1 đường truyền không tệ bạn có thể tải bằng phương thức Torrent để tránh lỗi.
+ Với đĩa CD, màn hình Boot có lựa chọn Check CD for detects để kiểm tra CD có lỗi hay không.

Kiểm tra CD có bị lỗi hay không ?


Mẹo :CD Ubuntu khá lớn nên xác suất lỗi là khá cao trong những phiên bản gần đây, vì thế dùng USB để cài đặt là phương pháp tối ưu hơn.
+ Ngoài ra, bạn cũng có thể gặp phải một vài trường hợp khác, không phải do vấn đề boot media, như không tương thức phần cứng chẳng hạn, bạn có tham khảo vài điều chỉnh Options lúc boot tại forum

    Ubuntu không nhận các phân vùng ổ cứng. 

Đây là một vấn đề khá thường gặp và cũng không đơn giản.Ổ cứng loại này thường gặp lỗi này do quá trình phân vùng trước đó không đúng nên GParted không nhận được các phân vùng, trong khi sử dụng lệnh sudo fdisk -l vẫn hiển thị các phân vùng bình thường.
Lỗi Partition Tables


Để khắc phục lỗi này không đơn giản, và có nguy cơ rất cao về việc mất dữ liệu (nếu làm không cẩn thận), vì thế bạn nên cân nhắc sử dụng phương án khác như Wubi, hoặc backup dữ liệu trước đó để phòng tránh bất trắc.
Bạn có thể tham khảo cách giải quyết ở đây hoặc ở đây 
Mẹo :Mượn bạn bè đâu đó một ổ cứng và backup dữ liệu trước khi thực hiện việc này
Khi xảy ra lỗi trong quá trình khôi phục , phải hết sức bình tĩnh, giữ nguyên, backup lại partition tables cũ (nếu có thể) và nhờ người có kinh nghiệm giúp đỡ.


    Cài đặt xong, nhưng không vào được Ubuntu, màn hình nhấp nháy liên tục, hoặc hiển thị "Out of range" 

Vấn đề này thường liên quan đến Card màn hình không tương thích, hoặc có lỗi Drivers với VGA của bạn.
Bạn có thể lần lượt thử một trong số các cách sau :
Khởi động lại, khi hiện màn hình lựa chọn của Grub, bạn chọn recovery mode thay thì lựa chọn mặc định.
Sau đó bạn chọn root hoặc netroot đều được, tiếp đó bạn gõ lệnh :

Xorg -configure

mv xorg.conf.new /etc/X11/xorg.conf

Với trường hợp màn hỉnh hiển thị "Out of range", bạn gõ tiếp lệnh sau để sửa file /etc/X11/xorg.conf

nano /etc/X11/xorg.conf

Bạn tìm đến mục Section "Screen" trong mục này bạn thêm đoạnModes "1024x768@85" Với 1024x768 là độ phân giải tối ưu cho màn hình của bạn (hoặc độ phân giải bạn muốn) và 85 là tần số quét của màn hình, thông thường với LCD là 60Hz, còn CRT là 70 - 85Hz.Nó sẽ tương tự thế này :

        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        SubSection "Display"
                Modes "1024x768@85"
                Viewport   0 0
                Depth     24
        EndSubSection

Nhấn Ctrl+X và chọn Yes để lưu lại.
Bạn khởi động lại máy và kiểm tra kết quả.
Sử dụng Ubuntu cơ bản
Terminal

Bài viết này sẽ hướng dẫn cho bạn hiểu được khái niệm về terminal, cách sử dụng, một vài lệnh cơ bản dùng trong terminal Terminal dịch ra tiếng Việt nghĩa là thiết bị đầu cuối.Một terminal giúp người dùng tương tác trực tiếp với các thiết bị phần cứng nào đó thông qua một giao diện dòng lệnh.Trong GNU/Linux, việc tương tác trực tiếp với phần cứng là nhiệm vụ của hạt nhân hệ điều hành, terminal đóng vai trò như một lớp tương tác cấp cao hơn.Do đó, người ta gọi thành phần này chính xác là Terminal Emulator.Nếu ai đã từng sử dụng hệ điều hành Windows của Microsoft sẽ thấy Terminal giống như Command Prompt (gọi tắt là cmd) hay cũng giống như một môi trường DOS cũ thu nhỏ.


Terminal1.png


Lợi thế của sử dụng cửa sổ dòng lệnh là tốc độ hoàn thành công việc nhanh hơn so với môi trường đồ hoạ.Khi cài đặt 1 gói nào đó với Synaptic Package Manager, bạn phải mất ít nhất 6 lần nhấn chuột và 1 lần nhập mật khẩu root.Nhưng với terminal, với lần nhấn chuột đầu tiên bạn chỉ cần viết 1 câu lệnh và nhập mật khẩu root.Và đó là tất cả.Gói của bạn sẽ được tải về và cài đặt ngay trong cửa sổ terminal.
Khởi độngTerminal

Trong Gnome (Ubuntu)

Terminal có thể tìm thấy ở Application menu -> Accessories -> Terminal.

Trong Xfce (Xubuntu)

Terminal có thể tìm thấy ở Application menu -> System -> Terminal.

Trong KDE (Kubuntu)

Terminal có thể tìm thấy ở KMenu -> System -> Terminal Program (Konsole).


Các tập lệnh
sudo

Hầu hết những lệnh sau đều cần mở đầu với lệnh sudo nếu bạn sắp làm việc với thư mục hoặc tập tin không thuộc về bạn.Lệnh này sẽ giúp bạn chạy các ứng dụng và lệnh với tư cách người dùng cao cấp : root (người mà có quyền làm bất cứ việc gì trên hệ thống của bạn ).Đây là một lênh đặc biệt cho phép bạn can thiệp vào những thiết lập của hệ thống trong một khoảng thời gian.Máy tính sẽ hỏi bạn mật khẩu đăng nhập (khi gõ, mật khẩu sẽ không hiện ra).Bạn cứ nhập Password và Enter là được .Sau khi sudo lần đầu tiên, thì sau đó một khoảng thời gian nhất định, bạn có thể sudo mà không cần gõ lại mật khẩu (Tất nhiên đó chỉ là khi bạn chưa tắt Terminal đi ).Vui lòng xem RootSudo và Sudo để biết thêm thông tin.Chú ý : Không nên lạm dụng sudo vì sudo chạy lệnh với tư cách người dùng cao cấp, và nó cho phép tác động đến toàn bộ hệ thống.Nếu không cẩn thận hệ thống của bạn có thể bị hỏng.Hãy thử chạy với tư cách người dùng bình thường rồi hãy sử dụng sudo !


Một số lệnh cơ bản

Cài đặt một gói

    sudo apt-get install tên-gói

hoặc

    sudo aptitude install tên-gói

thêm chi tiết về lệnh apt-get bạn có thể tìm thấy ở đây


Đổi mật khẩu

    sudo passwd têntàikhỏan


Lệnh tắt máy

    sudo shutdown -h now


Lệnh khởi động lại

    sudo reboot


Tắt một ứng dụng bị đơ

     xkill

Khi một ứng dụng nào đó bị đơ bạn có thể viết lệnh trên rồi di chuột đến cửa sổ của ứng dụng bị đơ rồi nhấn chuột trái, nhấn chuột phải để hủy bỏ.

Bạn có thể xem thêm các lệnh cơ bản trên Tờ ghi nhớ các lệnh cơ bản trong Ubuntu (tải tại đây).
Bạn có thể xem thêm về terminal ở đây
Ubuntu Software Center

Ubuntu Software Center (USC), một ứng dụng được tích hợp vào Ubuntu từ phiên bản Ubuntu 9.10.USC cung cấp cho bạn danh sách các phần mềm thông dụng được đánh giá mức thông dụng từ cao xuống thấp, giúp cho việc cài đặt Ubuntu dễ dàng hơn cho người mới sử dụng.Tuy nhiên máy bạn phải có kết nối Internet để phần mềm có thể kết nối tới kho lưu trữ phần mềm trực tuyến (repo), phần mềm sẽ tự động download về và cài vào máy bạn chỉ một cú click chuột.

Khởi động: Applications -> Ubuntu Software Center
Ubuntu Software Center.png

Sử dụng:

    Để cài đặt phần mềm bạn chỉ cần nhấn nút Install ở bên phải hoặc xem thông tin phần mềm đó bạn chỉ cần nhất nút More Info phí bên trái.

    Để gỡ bõ một phần mềm bạn nhất nút Remove ở phía bên phải.


Xem thêm cách sử dụng tại đây


Synaptics Package Manager và Software Sources
Synaptics Package Manager

Synaptics Package Manager (SPM) cũng với chức năng giống với Ubuntu Software Center (USC), nhưng SPM với khả năng quản lý chi tiết các gói phần mềm được cài, các gói cần nâng cấp, các gói chưa cài...Và cũng giống như USC, SPM cũng đòi hỏi máy bạn phải có kết nối Internet để phần mềm có thể cập nhật danh sách các gói phần mềm cài đặt và nâng cấp gói phần mềm từ Repo.


Khởi động: 'System -> Administrator -> Synaptics Packages Manager'
Synaptic-package-manager.png


Sử dụng:

    Để cài đặt một gói phần mềm: Click chuột trái vào gói phần mềm rồi chọn nút Apply, SPM tự động kiểm tra cái gói dependence chưa cài, bạn nhấn nút Apply một lần nữa để quá trình cài đặt bắt đầu.

Synaptic-confirm-install.png


    Gỡ bỏ một gói phần mềm: Click chuột phải vào gói phần mềm Mark for Removal, quá trình gỡ bỏ bắt đầu.Khi gỡ bỏ một gói phần mềm SPM sẽ tự động gỡ bỏ các gói dependence không còn được sử dụng cho các gói khác của gói đó. 

Software Sources

Software Sources (SS) là phần mềm quản lý các kết nối đến các kho phần mềm trực tuyến ở trên mạng.
 Khởi động: System -> Administrator -> Software Source

SS1.png
Sử dụng: Cách Add thêm repo của HanoiLug

    Vào trang http://virror.hanoilug.org/#ubuntu

deb http://virror.hanoilug.org/ubuntu/archive lucid main restricted universe multiverse
deb http://virror.hanoilug.org/ubuntu/archive lucid-updates main restricted universe multiverse

SS.png

    Nhấn vào nút Add, add từ dòng bạn vừa mới copy vào và nhấn nút Close, quá trình cập nhật bắt đầu.Cuối cùng bạn vào Synaptic và cài các gói từ repo của HanoiLug thôi.


Làm cho Ubuntu hoàn hảo hơn


www.howtoforge.com/the-perfect-desktop-ubuntu-10.04-lucid-lynx
Những câu hỏi thường gặp

Đây là những vấn đề mà người mới dùng Ubuntu hay hỏi nhất. Bạn hãy đọc thật kĩ chúng trước khi đặt câu hỏi. Chúc bạn có những giây phút hài lòng với Ubuntu!

Những câu hỏi thường gặp
Tài liệu tham khảo

Những tài liệu tham khảo được sử dụng để viết Beginner Guide 
