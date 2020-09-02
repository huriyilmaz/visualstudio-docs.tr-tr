---
title: 'Test alanı 1: kaynak denetiminden açmaya Ekle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e7b65eae0dcd71c2ad1bb3d72bf08ea90e69036a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64814585"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Test alanı 1: kaynak denetimine Ekle/aç
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu kaynak denetimi eklentisi test alanı, çözümlerin veya projelerin kaynak denetimi altına yerleştirilmesi ve bunları kaynak denetiminden almasını içerir.  
  
## <a name="command-menu-access"></a>Komut menüsü erişimi  
 Aşağıdaki [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tümleşik geliştirme ortamı menü yolları test durumlarında kullanılır:  
  
- İçin [!INCLUDE[vsvss](../../includes/vsvss-md.md)] , kaynak denetiminden Aç: **Dosya**, **Aç**, **Proje** / **çözümü**; konuma bakın [!INCLUDE[vsvss](../../includes/vsvss-md.md)] .  
  
- Diğer kaynak denetimi eklentileri için kaynak denetiminden Aç: **Dosya**, **kaynak denetimi**, **kaynak denetiminden Aç**.  
  
- Kaynak denetimine Ekle: **Dosya**, **kaynak denetimi**, **kaynak denetim dosyasına çözüm ekleme**, **kaynak**denetimi, **Seçili projeleri kaynak denetimine ekleme**.  
  
- Kısayol menüsü (proje/çözüm), **kaynak denetimine çözüm ekleyin**.  
  
- Kaynak denetiminden ekle: **Dosya**, **kaynak denetimi**, **kaynak denetiminden proje ekleme**.  
  
- İçin [!INCLUDE[vsvss](../../includes/vsvss-md.md)] , kaynak denetiminden Ekle ' de **Dosya**, **Ekle**, **Varolan proje**' de bulunabilir; [!INCLUDE[vsvss](../../includes/vsvss-md.md)] konuma bakın.  
  
    > [!NOTE]
    > Bu testte yerel bir dosyanın veya yerel bir IIS 'nin (Web sunucusu) bir yolu kullanılabilir.  
  
## <a name="expected-behavior"></a>Beklenen davranış  
  
- Desteklenen her proje türü için, bir Kullanıcı, kaynak denetiminden "ekleme" ve "açma" yapabilmelidir.  
  
- Kaynak denetimine bir proje eklendiğinde, karşılık gelen bir \<*ProjectName*> . vspscc dosyası (proje ipucu dosyası) oluşturulur. Dışlama dosya listesi ve bağlantı bilgilerini içerir. Projeye özgü bilgiler içerdiğinden bu dosyayı silmeyin.  
  
- Kaynak denetimine bir çözüm eklendiğinde, buna karşılık gelen \<*SolutionName*> . vssscc (Üçlü S) dosyası oluşturulur. Metin dosyası, proje ipucu dosyasına benzer şekilde bağlantı bilgilerini ve bir hariç tutma dosya listesini içerir. Bu dosya geçicidir ve yalnızca kaynak denetimi veritabanında bulunur.  
  
- Kaynak denetiminden bir çözüm açıldığında, \<*SolutionName*> geçici bir dosyada yerel olarak yalnızca kaynak denetim veritabanında bulunan bir. vsscc (çift S) dosyası oluşturulur. Bu dosya çözüm bağlantısı klasöründen çözüm dosyasına yolu içerir. Bu dosya geçicidir ve "kaynak denetiminden Aç" işlemi tamamlandığında yerel kopya silinir.  
  
- Kaynak denetimine bir proje eklendikten sonra, üzerinde herhangi bir kaynak denetimi eylemi gerçekleştirebilirsiniz (kullanıma alma, alma, vb.).  
  
## <a name="test-cases"></a>Test Çalışmaları  
 Kaynak denetimi test alanından Ekle/aç ' a yönelik özel test durumları aşağıda verilmiştir.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Durum 1a: kaynak denetimine çözüm ekleme  
 Bu test çalışması, kaynak denetimine çözüm eklemeye odaklanır.  
  
|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|  
|------------|----------------|--------------------------------|  
|Kaynak denetimine istemci projesi içeren çözüm ekleme|1. bir istemci projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetimine çözüm ekleme**).|Çözüm/proje kaynak denetimine eklendi.|  
|Kaynak denetimine bir dosya sistemi veya yerel IIS Web projesi içeren çözüm ekleme|1. bir dosya sistemi veya yerel IIS Web projesi oluşturun (projenin konumuna işaret etmek için gözatmayı kullanın; yol, ne tür bir Web projesi oluşturulacağını belirler).<br />2. çözümü kaynak denetimine ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetimine çözüm ekleme**).|Çözüm/proje kaynak denetimine eklendi.|  
|Kaynak denetimine uzak site Web projesi içeren çözüm ekleme|1. bir uzak site Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetimine çözüm ekleme**).<br />3. FrontPage erişim Uyarısı iletişim kutusunda **Tamam** ' a tıklayın.|Çözüm, kaynak denetimine eklendi.<br /><br /> Uzak site projesi kaynak denetimi altında DEĞIL. (Uzak site projelerinin kendi IIS sunucusundan denetlenmesi gerekir.)|  
|Kaynak denetimine **Seçili projeler Ekle**öğesini kullanarak kaynak denetimine tek bir proje çözümü ekleyin.|1. tek bir proje çözümü oluşturun.<br />2. yalnızca bir seçim olarak kaynak denetimine çözüm ekleyin (**Dosya**, **kaynak denetimi**, **Seçili projeleri kaynak denetimine Ekle**). Bu adım başarılı olursa sonraki adımla devam edin.<br />3. projeyi kaynak denetimine seçim olarak ekleyin (**Dosya**, **kaynak denetimi**, **Seçili projeleri kaynak denetimine Ekle**).<br />4. projeyi aynı konuma eklemek için **Evet** 'e tıklayın.<br />5. **düzenleme için kullanıma alma** Iletişim kutusunda **kullanıma** alma ' ya tıklayın.|`Result from Step 2:`<br /><br /> Projenin ve proje içindeki tüm dosyaların kullanıma alınmış kaynak denetimi göstergesi vardır ve araç Ipucu "kaynak denetimi altında değil" olarak görüntülenir.<br /><br /> `Result from Step 5:`<br /><br /> Proje ve çözüm dosyası kaynak denetimindeki aynı klasörslardır.|  
|Kaynak denetimine çözüm eklemeyi iptal et|1. tek bir proje çözümü oluşturun.<br />2. kaynak denetimine proje ve çözüm eklemeyi deneyin. Bu adım başarılı olursa sonraki adımla devam edin.<br />3. kaynak denetim sisteminden sonra iptal edin.|`Result from Step 2:`<br /><br /> Proje konumu kaynak denetimini ayarla iletişim kutusu yalnızca bir kez görünür.<br /><br /> `Result from Step 3:`<br /><br /> Proje ekleme iptal edildi, proje/çözüm kaynak denetimi altında DEĞIL ve tüm kaynak denetimi menüleri hala kullanılabilir.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>Durum 1B. Kaynak denetiminden çözüm aç  
 Bu test çalışması, çözümleri kaynak denetiminden açmaya odaklanır.  
  
|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|  
|------------|----------------|--------------------------------|  
|Kaynak denetiminden bir istemci projesi içeren bir çözüm açın|1. bir istemci projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. çözümü kaynak denetiminden yeni bir konuma açın.|Kaynak denetiminden açılan çözüm/proje.|  
|Kaynak denetiminden yerel veya IIS Web projesi içeren bir çözüm açın|1. yerel veya IIS Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. çözümü kaynak denetiminden yeni bir konuma açın.|Kaynak denetiminden açılan çözüm/proje.|  
|Kaynak denetiminden uzak site Web projesi içeren bir çözüm açın|1. bir uzak site Web projesi oluşturun.<br />2. çözümü kaynak denetimine ekleyin. Bu adım başarılı olursa sonraki adımla devam edin.<br />3. çözümü kapatın.<br />4. çözümü kaynak denetiminden yeni bir konuma açın.|`Result from Step 2:`<br /><br /> Uzak site Web, kaynak denetimi altında DEĞIL.<br /><br /> `Result from Step 4:`<br /><br /> Çözüm, kaynak denetiminden açıldı.<br /><br /> Uzak site projesi yüklendi, ancak kaynak denetimi altında DEĞIL.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Case 1C: kaynak denetiminden çözüm ekleme  
 Bu test çalışması, kaynak denetiminden çözüm eklemeye odaklanır.  
  
|Eylem|Test adımları|Doğrulanacak beklenen sonuçlar|  
|------------|----------------|--------------------------------|  
|Boş çözüme ekleme — tek bir proje çözümü|1. tek bir proje çözümü oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. ikinci boş bir çözüm oluşturun.<br />5. daha önce denetlenen çözümü kaynak denetiminden ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetiminden Proje Ekle**).|Eklenen proje **Çözüm Gezgini** görüntülenir ve iade edilir.|  
|Tek projem bir çözüme ekleme — tek proje|1. tek bir projeyle bir çözüm oluşturun.<br />2. çözümü kaynak denetimine ekleyin.<br />3. çözümü kapatın.<br />4. ikinci boş bir çözüm oluşturun.<br />5. daha önce denetlenen çözümü kaynak denetiminden ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetiminden Proje Ekle**).|Eklenen proje **Çözüm Gezgini** görüntülenir ve iade edilir.|  
|Çözüme ekleme — çözüm, seçime göre kaynak denetimine eklendi|1. bir projeyle bir çözüm oluşturun.<br />2. yalnızca kaynak denetimine seçim olarak çözüm ekleyin. Bu adım başarılı olursa sonraki adımla devam edin.<br />3. çözümü kapatın.<br />4. yeni bir çözüm oluşturun.<br />5. daha önce denetlenen çözümü kaynak denetiminden ekleyin (**Dosya**, **kaynak denetimi**, **kaynak denetiminden Proje Ekle**).|`Result from Step 2:`<br /><br /> Proje, kaynak denetimi altında değil.<br /><br /> `Result from Step 5:`<br /><br /> İlk çözüm çözüm öğeleri içeriyorsa, bunlar, kaynak denetiminden eklenemez, bu nedenle görünmez.<br /><br /> İlk çözümden proje kullanılamaz olarak görünür.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentileri için Test Kılavuzu](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
