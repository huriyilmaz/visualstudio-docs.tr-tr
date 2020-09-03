---
title: 'Nasıl yapılır: Kod Merkezi Premium kaynağıyla hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: db9a3e08e14e7fadca6df9e32361c0b042f565e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64783485"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Nasıl Yapılır: Kod Merkezi Birincil Kaynağı ile Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]Hata ayıklayıcı ile, MICROSOFT MSDN Code Center Premium 'da güvenli paylaşılan kaynakta hata ayıklaması yapabilirsiniz.  
  
 Bu konu başlığında, Visual Studio 'da kod Merkezi Premium kaynak kodu ayarlama ve hata ayıklama işlemlerinin nasıl yapılacağı açıklanmaktadır.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Kod Merkezi Premium ile hata ayıklamaya hazırlanmak için  
  
1. Akıllı kart okuyucunuzu bağlayın ve paylaşılan kaynak girişiminizden aldığınız kartı ekleyin.  
  
2. Visual Studio 'Yu başlatın.  
  
3. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.  
  
4. **Seçenekler** iletişim kutusunda, **hata ayıklama** düğümünü açın ve **genel**' e tıklayın.  
  
5. **Yalnızca kendi kodum etkinleştir (yalnızca yönetilen)** onay kutusunu temizleyin.  
  
6. **Kaynak sunucu desteğini etkinleştir**' i seçin.  
  
7. **Kaynak dosyalarının özgün sürümle tam olarak eşleşmesini gerektir**seçimini kaldırın.  
  
8. **Hata ayıklama** düğümü altında **semboller**' e tıklayın.  
  
9. **Sembol dosyası (. pdb) konumları** kutusunda, **Microsoft sunucu sembolleri** onay kutusunu temizleyin ve aşağıdaki konumları ekleyin:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Yolun sonuna sonundaki eğik çizgiyi eklediğinizden emin olun <strong>/</strong> .  
  
     Bu simgelerin önce yüklendiğinden emin olmak için bu konumları listenin en üstüne taşıyın.  
  
   > [!NOTE]
   > Bu kod Merkezi Premium konumlarının önce, yüklenen ilk konum olmaları için önce listelenmesi gerekir. Visual Studio 2010 ' de, **Microsoft symbol Servers** girişinin üzerinde herhangi bir sunucuyu taşıyamazsınız, bu nedenle onay kutusunu temizlemeniz gerekir.  
   > 
   >  Hata ayıklama oturumu sırasında Microsoft sembollerine sembolleri yüklemek için şunu yapın:  
   > 
   > 1. **Hata Ayıkla** menüsünde **Windows** ' u ve ardından **modüller**' i seçin.  
   >    2.  Sembolleri istediğiniz modülü seçin ve ardından kısayol menüsünü açın. **Sembolleri yükle** ' yi seçin ve ardından **Microsoft sembol sunucuları**' nı seçin.  
  
10. **Bu dizindeki sembol sunucularından önbellek sembolleri** kutusunda, `C:\symbols` Code Center Premium 'un sembolleri önbelleğe geçirebileceği gibi bir konum girin. Önbelleğe alma sembolleri, hata ayıklama sırasında performansı önemli ölçüde iyileştirebilir.  
  
     Bu yordamı tamamladıktan sonra kaynak kodu hata ayıklaması yaşarsanız [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , daha önce önbelleğe alınmış ve eski sembol dosyaları için önbellek konumunuzu denetleyin. Güncel olmayan sembol dosyalarını kaldırın.  
  
11. **Tamam**’a tıklayın.  
  
12. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Ayarların kalıcı olduğundan emin olmak için yeniden başlatın.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Işleme Iliştir kullanarak kaynak kodunuzda hata ayıklamak için  
  
1. Akıllı kart okuyucunuzu bağlayın ve paylaşılan kaynak girişiminizden aldığınız kartı ekleyin.  
  
2. Visual Studio 'Yu başlatın.  
  
3. Visual Studio projenizi açın.  
  
4. **Araçlar** menüsünde, **İşleme İliştir ' e**tıklayın.  
  
5. **Işleme İliştir** Iletişim kutusunda **Seç**' e tıklayın.  
  
6. **Kod türünü seç** iletişim kutusunda, **Bu kod türlerini Algıla**altında **Yerel**, **yönetilen**ve **yönetilen (v 4.0)** seçeneğini belirleyin.  
  
7. **Kod türünü seç** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.  
  
8. **Kullanılabilir işlemler** kutusunda, hata ayıklamak istediğiniz işlemi seçin.  
  
9. **Ekle**' ye tıklayın.  
  
10. Sertifikanızı onaylamanız istendiğinde, **Tamam**' a tıklayın. Sonra PIN 'inizi girin. İstenirse, kod Merkezi Premium için kullanım koşullarını kabul edin.  
  
     Simgeleri indirme, ağ hızına bağlı olarak çok zaman alabilir. Durum çubuğu, tüm simgelerin başarıyla indirildiğine işaret eder.  
  
11. Çözümünüzdeki tüm yönetilen projeler için iliştirme adımlarını yineleyin.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Mevcut bir çözümden kaynak kodunda hata ayıklamak için  
  
1. **Çözüm Gezgini**, çözüm için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. Çözüm Özellik sayfaları iletişim kutusunda, **ortak özellikler** düğümünde **Hata Ayıkla kaynak dosyaları** ' nı seçin.  
  
3. **Kaynak dosyaları Içeren dizinlere** aşağıdaki konumu ekleyin:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   > Yolun sonuna sonundaki eğik çizgiyi eklediğinizden emin olun <strong>/</strong> .  
  
4. Çözümünüzdeki yönetilen her proje için aşağıdakileri yapın  
  
   1. Çözüm Gezgini ' de, proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
   2. **Hata Ayıkla** ' yı seçin ve ardından yönetilmeyen **kod hata ayıklamayı etkinleştir**' i seçin.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Code Center Premium kaynağıyla çözümünüzde hata ayıklamak için  
  
1. `Package`Sınıfınıza paket oluşturucusunda bir kesme noktası ayarlayın.  
  
2. `Debug`Menüsünde, **hata ayıklamayı Başlat**' a tıklayın.  
  
3. Paket oluşturucusunda kesme noktasına ulaştığınızda, **çağrı yığını** penceresine gidin ve sembolleri yüklemek istediğiniz derlemenin yığın çerçevesini sağ tıklatın ve ardından **sembolleri yükle**' ye tıklayın.  
  
     Kaynağı yüklemek için çağrı çerçevesine çift tıklayın.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Kod Merkezi Premium 'da kaynak koda gitmek için  
  
1. Akıllı kart okuyucunuzu bağlayın ve paylaşılan kaynak girişiminizden aldığınız kartı ekleyin.  
  
2. Internet Explorer 'ı başlatın aşağıdaki URL 'YI girin: `https://codepremium.msdn.microsoft.com`  
  
3. İstediğiniz kaynağı bulmak için gidin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)   
 [Kod Merkezi Premium](https://www.microsoft.com/en-us/sharedsource/code-center-premium.aspx)
