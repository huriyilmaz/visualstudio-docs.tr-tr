---
title: İş parçacıklarında ve işlemlerde hata ayıklamaya | Microsoft Docs
description: İş parçacıklarında ve işlemlerde hata ayıklamaya yönelik araçları Visual Studio. İş parçacıkları ve işlemler, belirli bir sırada yürütmesi gereken yönergeler dizilerini temsil eder.
ms.custom: SEO-VS-2020
ms.date: 04/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e1a377550b43d6f746e609586561a3dfb5046089
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105420"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>İş parçacıklarında ve işlemlerde hata ayıklamaya Visual Studio
*İş* parçacıkları *ve süreçler,* bilgisayar bilimiyle ilgili kavramlardır. Her ikisi de belirli bir sırayla yürütmesi gereken yönergeler dizilerini temsil eder. Ancak, ayrı iş parçacıklarında veya işlemlerde yönergeler paralel olarak yürütülür.

 İşlemler işletim sisteminde mevcuttur ve kullanıcıların program veya uygulama olarak neleri göreceğine karşılık gelen işlemlerdir. Öte yandan bir iş parçacığı bir işlem içinde mevcuttur. Bu nedenle, iş parçacıkları bazen hafif *işlemler olarak adlandırılır.* Her işlem bir veya daha fazla iş parçacığı içerir.

 Birden çok işlem olması, bir bilgisayarın aynı anda birden fazla görev gerçekleştirmelerini sağlar. Birden çok iş parçacığının varlığı, bir işlemi paralel olarak gerçekleştirilecek işi ayırmaya olanak sağlar. Çok işlemcili bir bilgisayarda işlemler veya iş parçacıkları farklı işlemcilerde çalışır. Bu, gerçek paralel işlemeyi sağlar.

 Kusursuz paralel işleme her zaman mümkün değildir. İş parçacıkları bazen eşitlenmeli. Bir iş parçacığının başka bir iş parçacığından gelen sonucu beklemesi veya bir iş parçacığının başka bir iş parçacığının kullanmakta olduğu kaynağa özel erişimi olabilir. Eşitleme sorunları, çok iş parçacıklı uygulamalarda hataların yaygın bir nedenidir. Bazen iş parçacıkları, hiçbir zaman kullanılabilir hale gelir bir kaynak için beklemeye neden olabilir. Bu durum kilitlenme adlı bir *koşula neden olur.*

 Hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayıklayıcısı, iş parçacıklarında ve işlemlerde hata ayıklamak için güçlü ancak kullanımı kolay araçlar sağlar.

## <a name="tools-and-features"></a>Araçlar ve özellikler
içinde kullanmak istediğiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] araçlar, hata ayıklamaya çalıştığın kod türüne bağlıdır:

- İşlemler için birincil araçlar İşleme Ekle **iletişim** kutusu, **İşlemler penceresi ve** Hata Ayıklama Konumu araç **çubuğu'larıdır.**

- İş parçacıklarında hata ayıklamaya yardımcı  olan birincil araçlar İş Parçacıkları penceresi, kaynak pencerelerde iş parçacığı işaretçileri, **Paralel** Yığınlar penceresi, **Paralel** İzleme penceresi ve Hata Ayıklama Konumu araç çubuğu'larıdır. 

- Görev Paralel <xref:System.Threading.Tasks.Task> [Kitaplığı'nda (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl)kullanan kodlar için, [Eşzamanlılık Çalışma Zamanı](/cpp/parallel/concrt/concurrency-runtime/) (yerel kod),    çok iş parçacıklı uygulamalarda hata ayıklamak  için birincil araçlar Paralel Yığınlar penceresi, Paralel İzleme penceresi ve Görevler penceresidir (Görevler penceresi JavaScript promise nesnesini de destekler).

- GPU'da iş parçacıklarında hata ayıklama için birincil araç GPU İş Parçacıkları **pencereleridir.**

  Aşağıdaki tabloda, kullanılabilir bilgiler ve bu yerlerin her birsinde gerçekleştirebilirsiniz eylemler yer alır:

|Kullanıcı Arabirimi|Kullanılabilir Bilgiler|Gerçekleştirin Eylemler|
|--------------------|---------------------------|-----------------------------|
|**İşleme Ekle** iletişim kutusu|Şu işlemlere ek işlemler abilirsiniz:<br /><br /> - İşlem adı (.exe)<br />- İşlem kimliği numarası<br />- Menü Çubuğu Başlığı<br />- Tür (Yönetilen v4.0; Yönetilen v2.0, v1.1, v1.0; x86; x64; IA64)<br />- Kullanıcı Adı (hesap adı)<br />- Oturum numarası|Eklemek istediğiniz işlemi seçin<br /><br /> Uzak bilgisayar seçme<br /><br /> Uzak bilgisayarlara bağlanmak için aktarım türünü değiştirme|
|**İşlemler** penceresi|Ekli İşlemler:<br /><br /> - İşlem Adı<br />- İşlem kimliği numarası<br />- İşlem yolu .exe<br />- Menü Çubuğu Başlığı<br />- Durum (Kesme. Çalışıyor)<br />- Hata Ayıklama (Yerel, Yönetilen ve bu şekilde devam ediyor.)<br />- Aktarım türü (varsayılan, kimlik doğrulaması olmayan yerel)<br />- Aktarım Niteleyicisi (uzak bilgisayar)|Araçları:<br /><br /> - Ekleme<br />- Ayırma<br />- Sonlandırma<br /><br /> Kısayol menüsü:<br /><br /> - Ekleme<br />- Ayırma<br />- Hata ayıklama durdurulurken ayırma<br />- Sonlandırma|
|**İş parçacıkları** penceresi|Geçerli işlemde iş parçacıkları:<br /><br /> - İş Parçacığı Kimliği<br />- Yönetilen Kimlik<br />- Kategori (ana iş parçacığı, arabirim iş parçacığı, uzaktan yordam çağrısı işleyicisi veya çalışan iş parçacığı)<br />- İş Parçacığı Adı<br />- İş parçacığının oluşturulacak konumu<br />- Öncelik<br />- Benzeşm Maskesi<br />- Askıya Alınan Sayı<br />- İşlem Adı<br />- Bayrak Göstergesi<br />- Askıya alınmış gösterge|Araçları:<br /><br /> - Arama<br />- Arama Çağrı Yığını<br />- Bayrak Yalnızca kendi kodum<br />- Özel Modül Seçimi bayrağı oluşturma<br />- Grupla<br />- Sütunlar<br />- Çağrı yığınlarını genişletme/daraltma<br />- Grupları genişletme/daraltma<br />- İş Parçacıklarını Dondurma/Çözme<br /><br /> Kısayol menüsü:<br /><br /> - İş parçacıklarını kaynakta gösterme<br />- İş parçacığına geçiş<br />- Çalışan bir iş parçacığını dondurma<br />- Donmuş iş parçacığını çözme<br />- Ek çalışma için iş parçacığına bayrak uygulama<br />- bir iş parçacığının bayrağını açma<br />- bir iş parçacığını yeniden adlandırma<br />- İş parçacıklarını gösterme ve gizleme<br /><br /> Diğer eylemler:<br /><br /> - DataTip'te bir iş parçacığı için çağrı yığınını görüntüleme|
|Kaynak penceresi|Sol oluklu iş parçacığı göstergeleri tek veya birden çok iş parçacığını gösterir (varsayılan olarak, İş Parçacıkları penceresinde kısayol menüsü kullanılarak **açık)**|Kısayol menüsü:<br /><br /> -Bir iş parçacığına geçiş yap<br />-Ek çalışma için bir iş parçacığına bayrak ekleyin<br />-Bir iş parçacığının bayrağını kaldır|
|**Hata ayıklama konumu** araç çubuğu|-Geçerli işlem<br />-Uygulamayı askıya alma<br />-Uygulamayı sürdürür<br />-Uygulamayı askıya alma ve kapatma<br />-Geçerli iş parçacığı<br />-Geçerli iş parçacığı bayrak durumunu değiştirme<br />-Yalnızca bayraklı iş parçacıklarını göster<br />-Yalnızca geçerli işlemi göster<br />-Geçerli yığın çerçevesi|-Başka bir işleme geçiş yap<br />-Uygulamayı askıya alma, sürdürme veya kapatma<br />-Geçerli işlemde başka bir iş parçacığına geçiş yap<br />-Geçerli iş parçacığında başka bir yığın çerçevesine geçiş yap<br />-Geçerli iş parçacıklarını işaretle veya bayrak kaldır<br />-Yalnızca bayraklı iş parçacıklarını göster<br />-Yalnızca geçerli işlemi göster|
|**Paralel Yığınlar** penceresi|-Birden çok iş parçacığı için yığınları tek bir pencerede çağırın.<br />-Her iş parçacığı için etkin yığın çerçevesi.<br />-Her bir yöntem için çağıranlar ve Callet 'ler.|-Belirtilen iş parçacıklarını filtrele<br />-Görevler görünümüne geç<br />-Bir iş parçacığını işaretle veya bayrak kaldır<br />-Yakınlaştır|
|**Paralel izleme** penceresi|-Özel dikkat etmek istediğiniz bir iş parçacığını işaretlemek için kullanabileceğiniz bayrak sütunu.<br />-Bir okun seçili çerçeveyi gösterdiği çerçeve sütunu.<br />-Makine, işlem, kutucuk, görev ve iş parçacığını görüntüleyebilen yapılandırılabilir bir sütun.|-Bir iş parçacığını işaretle veya bayrak kaldır<br />-Yalnızca bayraklı iş parçacıklarını göster<br />-Kare değiştirme<br />-Bir sütunu sıralama<br />-Grup iş parçacıkları<br />-İş parçacıklarını dondurma veya çözme<br />-Paralel izleme penceresi verileri dışarı aktarma|
|**Görevler** penceresi|- <xref:System.Threading.Tasks.Task> Görev kimliği, görev durumu (zamanlanmış, çalışan, bekleme, kilitli) ve göreve atanan iş parçacığını içeren nesneler hakkında bilgileri görüntüleyin.<br />-Çağrı yığınında geçerli konum.<br />-Temsilci oluşturma zamanında göreve geçildi|-Geçerli göreve geçiş yap<br />-Bir görevi işaretle veya bayrak kaldır<br />-Bir görevi dondurma veya çözme|
|**GPU Iş parçacıkları** penceresi|-Özel dikkat etmek istediğiniz bir iş parçacığını işaretlemek için kullanabileceğiniz bayrak sütunu.<br />-Sarı okun geçerli iş parçacığını gösterdiği geçerli iş parçacığı sütunu.<br />-Aynı konumdaki iş parçacığı sayısını görüntüleyen **Iş parçacığı sayısı** sütunu.<br />-Her iş parçacığı grubunun bulunduğu kod satırını görüntüleyen **satır** sütunu.<br />-Her iş parçacığı grubunun bulunduğu yönerge adresini görüntüleyen **Adres** sütunu.<br />-Adresin kodundaki konum olan **Location** sütunu.<br />-İş parçacığının etkin veya engellenmiş olduğunu gösteren **durum** sütunu.<br />-Satırdaki iş parçacıkları için döşeme dizinini gösteren **döşeme** sütunu.|-Farklı bir iş parçacığına geçiş yapın<br />-Belirli bir kutucuğu ve iş parçacığını görüntüleme<br />-Bir sütunu görüntüleme veya gizleme<br />-Sütuna göre sırala<br />-Grup iş parçacıkları<br />-İş parçacıklarını dondurma veya çözme<br />-Bir iş parçacığını işaretle veya bayrak kaldır<br />-Yalnızca bayraklı iş parçacıklarını göster|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Çok Iş parçacıklı uygulamalarda hata ayıklama](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [GPU Kodunda Hata Ayıklama](../debugger/debugging-gpu-code.md)