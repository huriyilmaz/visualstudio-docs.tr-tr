---
title: 'Nasıl yapılır: hata Işaretleyicileri uygulama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - error markers
ms.assetid: e8e78514-5720-4fc2-aa43-00b6af482e38
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2af9e0765fb5bc73a35bebfc2f50f5d2a41122d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64803619"
---
# <a name="how-to-implement-error-markers"></a>Nasıl Yapılır: Hata İşaretçilerini Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata işaretçileri (veya kırmızı dalgalı alt çizgiler), uygulanacak metin düzenleyici özelleştirmelerinin en zor sayısıdır. Ancak, VSPackage kullanıcılarına sundukları avantajlar, bu maliyetleri sağlamak için maliyeti en uygun şekilde gerçekleştirebilir. Hata işaretçileri, dil ayrıştırıcılarınızın, dalgalı veya dalgalı kırmızı bir çizgiyle yanlış bir biçimde işaret eden metni daha güvenli bir şekilde işaretler. Bu gösterge, programcıların hatalı kodu görsel olarak görüntüleyerek yardımcı olur.  
  
 Kırmızı dalgalı alt çizgileri uygulamak için metin işaretçilerini kullanın. Kural olarak, dil Hizmetleri metin arabelleğine, boş zamanlı veya bir arka plan iş parçacığında bir arka plan geçişi olarak kırmızı dalgalı alt çizgiler ekler.  
  
### <a name="to-implement-the-red-wavy-underline-feature"></a>Kırmızı dalgalı çizili özelliği uygulamak için  
  
1. Kırmızı dalgalı alt çizgiyi yerleştirmek istediğiniz metni seçin.  
  
2. Türün işaretçisini oluşturun `MARKER_CODESENSE_ERROR` . Daha fazla bilgi için bkz. [nasıl yapılır: standart metin Işaretçileri ekleme](../extensibility/how-to-add-standard-text-markers.md).  
  
3. Bundan sonra bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> arabirim işaretçisi geçirin.  
  
   Bu işlem, belirli bir işaretçi üzerinde ipucu metni veya özel bağlam menüsü oluşturmanıza de olanak tanır. Daha fazla bilgi için bkz. [nasıl yapılır: standart metin Işaretçileri ekleme](../extensibility/how-to-add-standard-text-markers.md).  
  
   Hata işaretçilerinin görüntülenebilmesi için aşağıdaki nesneler gereklidir.  
  
- Bir ayrıştırıcı.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2>Yeniden ayrıştırılacak satırları tanımlamak için satır bilgilerinde değişiklik kayıtlarını tutan bir görev sağlayıcısı (yani bir uygulamasıdır).  
  
- Yöntemini kullanarak görünümden giriş işareti değişiklik olaylarını yakalayan bir metin görünümü filtresi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewEvents.OnChangeCaretLine%2A> .  
  
  Ayrıştırıcı, görev sağlayıcısı ve filtre, hata işaretçileri mümkün hale getirmek için gereken altyapıyı sağlar. Aşağıdaki adımlar, hata işaretleyicilerini görüntüleme sürecini sağlar.  
  
1. Filtrelenen bir görünümde filtre, bu görünümün verileriyle ilişkili görev sağlayıcısına bir işaretçi alır.  
  
    > [!NOTE]
    > Yöntem ipuçları, ekstre tamamlama, hata işaretçileri vb. için aynı komut filtresini kullanabilirsiniz.  
  
2. Filtre başka bir satıra taşındığını belirten bir olay aldığında, hataları denetlemek için bir görev oluşturulur.  
  
3. Görev işleyicisi, çizginin kirli olup olmadığını denetler. Öyleyse, hata için satırı ayrıştırır.  
  
4. Hata bulunursa, görev sağlayıcısı bir görev öğesi örneği oluşturur. Bu örnek, ortamın metin görünümünde bir hata işaretleyicisi olarak kullandığı metin işaretleyicisini oluşturur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eski API ile metin Işaretleyicileri kullanma](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Nasıl yapılır: standart metin Işaretçileri ekleme](../extensibility/how-to-add-standard-text-markers.md)   
 [Nasıl yapılır: özel metin Işaretçileri oluşturma](../extensibility/how-to-create-custom-text-markers.md)   
 [Nasıl Yapılır: Metin İşaretçileri Kullanma](../extensibility/how-to-use-text-markers.md)
