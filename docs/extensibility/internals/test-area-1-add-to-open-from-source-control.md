---
title: 'Test Alanı 1: Kaynak Denetiminden Açık Ekle | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ac7b8e5a60fe25ac22272cc28fc3ed6f903b058
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704675"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Test Alanı 1: Kaynak Denetimine Ekle/Aç
Bu kaynak denetimi eklentisi test alanı, çözümleri veya projeleri kaynak denetimi altına yerleştirmeyi ve kaynak denetiminden almalarını kapsar.

## <a name="command-menu-access"></a>Komut Menüsü ne erişim
 Test [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] servis örneklerinde aşağıdaki tümleşik geliştirme ortamı menü yolları kullanılır:

- Kaynak [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]kontrolünden açık için: **Dosya**, **Aç**, **Proje**/**Çözümü**; [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] konuma bakın.

- Diğer kaynak kontrol eklentileri için, kaynak kontrolünden açık: **Dosya**, **Kaynak Denetimi**, **Kaynak Denetimi'nden açık**.

- Kaynak denetimine ekle: **Dosya**, **Kaynak Denetimi**, Kaynak **Denetim Dosyasına Çözüm Ekle**, Kaynak **Denetimi**, **Seçili Projeleri Kaynak Denetimine Ekle**.

- Kısayol Menüsü (Proje/Çözüm), **Kaynak Denetimine Çözüm Ekleyin.**

- Kaynak denetiminden ekle: **Dosya**, **Kaynak Denetimi**, **Kaynak Denetimi'nden Proje Ekle**.

- Için [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], kaynak denetiminden ekle de **Dosya**mevcuttur , **Ekle**, **Mevcut Proje**; [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] konuma bakın.

  > [!NOTE]
  > Bu testte yerel bir dosyanın yolu veya yerel bir IIS (web sunucusu) kullanılabilir.

## <a name="expected-behavior"></a>Beklenen Davranış

- Desteklenen her proje türü için, bir kullanıcı "Ekle" ve "Aç from from" Kaynak Denetimi yapabilmelidir.

- Bir proje Kaynak Denetimi'ne eklendiğinde, ilgili \< *projectname*>.vspscc dosyası (Project ipucu dosyası) oluşturulur. Dışlama dosya listesi ve bağlantı bilgileri içerir. Projeye özgü bilgiler içerdiğinden bu dosyayı silmeyin.

- Kaynak denetimine bir çözüm eklendiğinde, ilgili \< *solutionname*>.vssscc (üçlü S) dosyası oluşturulur. Metin dosyası, proje ipucu dosyasına benzer bağlantı bilgileri ve bir dışlama dosya listesi içerir. Bu dosya geçicidir ve yalnızca kaynak denetim veritabanında bulunur.

- Bir çözüm kaynak denetiminden açıldığında, yalnızca kaynak denetim veritabanında bulunan \< *solutionname*>.vsscc (çift S) dosyası geçici bir dosyada yerel olarak oluşturulur. Bu dosya, çözüm bağlantısı klasöründen çözüm dosyasına giden yolu içerir. Bu dosya geçicidir ve "Kaynak Denetimden Aç" işlemi tamamlandığında yerel kopya silinir.

- Bir proje kaynak denetimine eklendikten sonra, üzerinde herhangi bir kaynak denetimi eylemi gerçekleştirebilirsiniz (Kullanıma Alma, Get, vb.).

## <a name="test-cases"></a>Test Çalışmaları
 Kaynak Denetiminden Ekle/Aç test alanı için özel test örnekleri aşağıda veda edilebistir.

### <a name="case-1a-add-solution-to-source-control"></a>Örnek 1a: Kaynak Denetimine Çözüm Ekle
 Bu test çalışması, kaynak denetimine çözümler eklemeye odaklanır.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetimine istemci projesi içeren çözüm ekleme|1. Bir istemci projesi oluşturun.<br />2. Çözüm kaynak denetimine ekleyin (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimine Çözüm Ekle**).|Çözüm/Proje kaynak denetimine eklendi.|
|Kaynak denetimine Dosya Sistemi veya yerel IIS Web projesi içeren çözüm ekleme|1. Bir Dosya Sistemi veya yerel IIS Web projesi oluşturun (projenin konumunu belirtmek için Gözat düğmesini kullanın; yol ne tür Bir Web projesi oluşturulduğunu belirler).<br />2. Çözüm kaynak denetimine ekleyin (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimine Çözüm Ekle**).|Çözüm/Proje kaynak denetimine eklendi.|
|Kaynak denetimine Uzak Site Web projesi içeren çözüm ekleme|1. Uzak Bir Site Web projesi oluşturun.<br />2. Çözüm kaynak denetimine ekleyin (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimine Çözüm Ekle**).<br />3. FrontPage Access uyarı iletişim kutusunda **Tamam'ı** tıklatın.|Çözüm kaynak denetimine eklendi.<br /><br /> Uzak Site projesi kaynak kontrolü altında DeğİlDİr. (Uzak Site projeleri kendi IIS sunucularından kontrol edilmelidir.)|
|**Kaynak Denetimine Seçili Projeleri Ekle'yi**kullanarak kaynak denetimine tek bir proje çözümü ekleyin.|1. Tek bir proje çözümü oluşturun.<br />2. Seçim olarak kaynak denetimine yalnızca çözüm ekleyin (**Dosya**, **Kaynak Denetimi**, **Seçili Projeleri Kaynak Denetimine Ekle**). Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />3. Seçim olarak kaynak denetimine proje ekleme (**Dosya**, **Kaynak Denetimi**, **Seçili Projeleri Kaynak Denetimine Ekle**).<br />4. Projeyi aynı konuma eklemek için **Evet'i** tıklatın.<br />5. **Yap iletişim** kutusunu yeniden ele alametinde Kullanıma **Ala'yı** tıklatın.|`Result from Step 2:`<br /><br /> Proje ve proje içindeki tüm dosyaların denetlenen bir kaynak denetim göstergesi vardır ve Araç İpucu "Kaynak denetimi altında değil" görüntüler.<br /><br /> `Result from Step 5:`<br /><br /> Proje ve çözüm dosyası kaynak denetiminde aynı klasördedir.|
|Kaynak denetimine çözüm eklemeyi iptal etme|1. Tek bir proje çözümü oluşturun.<br />2. Kaynak denetimine proje ve çözüm eklemeye çalış. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />3. Kaynak kontrol sisteminde n için iptal edin.|`Result from Step 2:`<br /><br /> Proje konumu denetim kutusunu ayarla yalnızca bir kez görüntülenir.<br /><br /> `Result from Step 3:`<br /><br /> Proje iptal, proje / çözüm kaynak denetimi altında DeğİlDİr ve tüm kaynak denetim menüleri hala kullanılabilir ekle.|

### <a name="case-1b-open-solution-from-source-control"></a>Dava 1b. Kaynak Kontrolünden Açık Çözüm
 Bu test çalışması, kaynak denetiminden gelen çözümleri açmaya odaklanır.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Kaynak denetiminden istemci projesi içeren bir çözüm açma|1. Bir istemci projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. Çözümü kaynak kontrolünden yeni bir konuma açın.|Çözüm/Proje kaynak kontrolünden açıldı.|
|Kaynak denetiminden yerel veya IIS Web projesi içeren bir çözüm açma|1. Yerel veya IIS Web projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. Çözümü kaynak kontrolünden yeni bir konuma açın.|Çözüm/Proje kaynak kontrolünden açıldı.|
|Kaynak denetiminden Uzak Site Web projesi içeren bir çözüm açma|1. Uzak Bir Site Web projesi oluşturun.<br />2. Çözümü kaynak denetimine ekleyin. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />3. Çözümü kapatın.<br />4. Çözümü kaynak kontrolünden yeni bir konuma açın.|`Result from Step 2:`<br /><br /> Uzak Site Web kaynak kontrolü altında DeğİlDİ.<br /><br /> `Result from Step 4:`<br /><br /> Çözüm kaynak kontrolünden açıldı.<br /><br /> Uzak Site projesi yüklenir, ancak kaynak denetimi altında DeğİlDİr.|

### <a name="case-1c-add-solution-from-source-control"></a>Büyük/Küçük Harf 1c: Kaynak Denetiminden Çözüm Ekle
 Bu test çalışması, kaynak denetiminden çözümler eklemeye odaklanır.

|Eylem|Test Adımları|Doğrulaması Beklenen Sonuçlar|
|------------|----------------|--------------------------------|
|Boş çözüme ekle — tek bir proje çözümü|1. Tek bir proje çözümü oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. İkinci bir boş çözüm oluşturun.<br />5. Kaynak kontrolünden önceden denetlenen çözümü ekleyin (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimi'nden Proje Ekle**).|Eklenen proje Çözüm **Gezgini'nde** görünür ve iade edilir.|
|Tek projeile çözüme ekleme — tek proje|1. Tek bir proje ile bir çözüm oluşturun.<br />2. Çözümü kaynak denetimine ekleyin.<br />3. Çözümü kapatın.<br />4. İkinci bir boş çözüm oluşturun.<br />5. Kaynak kontrolünden önceden denetlenen çözümü ekleyin (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimi'nden Proje Ekle**).|Eklenen proje Çözüm **Gezgini'nde** görünür ve iade edilir.|
|Çözüme ekle — çözüm seçimle kaynak denetimine eklendi|1. Bir proje ile bir çözüm oluşturun.<br />2. Seçim olarak kaynak denetimine yalnızca çözüm ekleyin. Bu adım başarılı olursa, bir sonraki adıma devam edin.<br />3. Çözümü kapatın.<br />4. Yeni bir çözüm oluşturun.<br />5. Kaynak kontrolünden önceden denetlenen çözümü ekleyin (**Dosya**, **Kaynak Denetimi**, **Kaynak Denetimi'nden Proje Ekle**).|`Result from Step 2:`<br /><br /> Proje kaynak denetimi altında değildir.<br /><br /> `Result from Step 5:`<br /><br /> İlk çözümde çözüm öğeleri varsa, kaynak denetiminden eklenemezler, bu nedenle görünmezler.<br /><br /> İlk çözümden proje kullanılamaz olarak görünür.|

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
