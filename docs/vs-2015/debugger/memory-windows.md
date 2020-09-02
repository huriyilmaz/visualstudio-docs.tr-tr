---
title: Bellek pencereleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.memory
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
caps.latest.revision: 37
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e60f9b3c9acf1377139fee27486bb10251d8804a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158467"
---
# <a name="memory-windows"></a>Bellek Pencereleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Bellek** penceresi, uygulamanız tarafından kullanılan bellek alanına bir görünüm sağlar. **İzle** penceresi, **Hızlı bakış** iletişim kutusu, **oto** penceresi ve **Yereller** penceresi, bellekteki belirli konumlarda depolanan değişkenlerin içeriğini gösterir. Ancak, **bellek** penceresi size büyük ölçekli resmi gösterir. Bu görünüm, diğer Windows 'da iyi olmayan büyük veri parçalarını (örneğin, arabellek veya büyük dizeler) incelemek için kullanışlı olabilir. Ancak, **bellek** penceresi verileri görüntüleme ile sınırlı değildir. İçeriğin atanmamış bellekte veri, kod veya rastgele bir atık bit olup olmadığı, bellek alanında her şeyi görüntüler.  
  
 **Bellek** penceresi yalnızca, **Seçenekler** Iletişim kutusunda,**hata ayıklama** düğümünde adres düzeyi hata ayıklama etkinse kullanılabilir. Bellek **kavramı** , bellek kavramını tanımayan diller olan BETIK veya SQL için kullanılamaz.  
  
## <a name="opening-a-memory-window"></a>Bellek penceresi açma  
  
#### <a name="to-open-a-memory-window"></a>Bellek penceresi açmak için  
  
1. Zaten hata ayıklama modunda değilseniz, hata ayıklamayı başlatın.  
  
2. **Hata Ayıkla** menüsünde **Windows**' a işaret edin. Daha sonra, **bellek** üzerine gelin ve **bellek 1**, **bellek 2**, **bellek 3**veya **bellek 4**' e tıklayın. (Alt düzey sürümlerinde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yalnızca tek bir **bellek** penceresi vardır. Bu sürümlerden birini kullanıyorsanız, yalnızca **bellek**' e tıklamanız yeterlidir.)  
  
## <a name="paging-in-the-memory-window"></a>Bellek penceresinde sayfalama  
 **Bellek** penceresinde standart olmayan bir şekilde çalışan dikey bir kaydırma çubuğu vardır. Modern bir bilgisayarın adres alanı çok büyük olduğundan, ScrollBar kaydırma çubuğunu yakalayıp ve rastgele bir konuma sürükleyerek kolayca kaybedilirsiniz. Bu nedenle, Thumb "yay-yüklendi" olur ve her zaman kaydırma çubuğunun merkezinde kalır. Yerel kod uygulamalarında, sayfa yukarı veya aşağı taşıyabilirsiniz, ancak serbestçe ilerlenemez.  
  
 Daha yüksek bellek adresleri pencerenin alt kısmında görünür. Daha yüksek bir adresi görüntülemek için aşağı kaydırın.  
  
#### <a name="to-page-up-or-down-in-memory"></a>Bellekte sayfa yukarı veya aşağı  
  
1. Sayfa aşağı (daha yüksek bir bellek adresine taşı) için dikey kaydırma çubuğunun altındaki Thumb öğesine tıklayın.  
  
2. Sayfa yukarı (daha düşük bir bellek adresine taşı) için üst kaydırma çubuğunun üzerine tıklayın.  
  
## <a name="selecting-a-memory-location"></a>Bellek konumu seçme  
 Bellekteki seçili bir konuma anında geçmek istiyorsanız, bir sürükle ve bırak işlemi kullanarak veya **Adres** kutusundaki değeri düzenleyerek bunu yapabilirsiniz. **Adres** kutusu yalnızca sayısal değerler değil, ayrıca adresleri değerlendiren ifadeleri de kabul eder. Varsayılan olarak, **bellek** penceresi bir **Adres** ifadesini, programınız çalışırken yeniden değerlendirerek canlı bir ifade olarak değerlendirir. Canlı ifadeler çok faydalı olabilir. Örneğin, bir işaretçi tarafından dokunarak belleği görüntülemek için bunları kullanabilirsiniz.  
  
#### <a name="to-select-a-memory-location-by-dragging-and-dropping"></a>Sürükleyip bırakarak bir bellek konumu seçmek için  
  
1. Herhangi bir pencerede, bellek adresini içeren bir bellek adresi veya işaretçi değişkeni seçin.  
  
2. Adresi veya işaretçiyi **bellek** penceresine sürükleyin.  
  
#### <a name="to-select-a-memory-location-by-editing"></a>Bir bellek konumunu düzenleyerek seçin  
  
1. **Bellek** penceresinde **Adres** kutusunu seçin.  
  
2. Görmek istediğiniz adresi yazın veya yapıştırın ve ardından **ENTER**tuşuna basın.  
  
## <a name="changing-the-way-the-memory-window-displays-information"></a>Bellek penceresinin bilgileri görüntüleme biçimini değiştirme  
 **Bellek** penceresinin bellek içeriğini gösterir biçimini özelleştirebilirsiniz. Varsayılan olarak, bellek içerikleri onaltılık biçimde tek baytlık tamsayılar olarak görünür ve sütun sayısı pencerenin geçerli genişliği tarafından otomatik olarak belirlenir.  
  
#### <a name="to-change-the-format-of-the-memory-contents"></a>Bellek içeriklerinin biçimini değiştirmek için  
  
1. **Bellek** penceresine sağ tıklayın.  
  
2. İstediğiniz biçimi seçin.  
  
#### <a name="to-change-the-number-of-columns-in-the-memory-window"></a>Bellek penceresindeki sütun sayısını değiştirmek için  
  
1. **Bellek** penceresinin en üstündeki araç çubuğunda, **sütunlar** listesini bulun.  
  
2. **Sütunlar** listesinde, göstermek istediğiniz sütun sayısını seçin veya pencerenin genişliğine uyacak şekilde otomatik ayarlama için **Otomatik** ' i seçin.  
  
   Programınız çalışırken **bellek** penceresinin içeriğinin değiştirilmesini istemiyorsanız, canlı ifade değerlendirmesini devre dışı bırakabilirsiniz.  
  
#### <a name="to-toggle-live-evaluation"></a>Canlı değerlendirmeyi değiştirmek için  
  
1. **Bellek** penceresine sağ tıklayın.  
  
2. Kısayol menüsünde **otomatik olarak**yeniden değerlendir ' e tıklayın.  
  
    Canlı değerlendirme açık ise, seçenek seçilir ve etkin değerlendirmeyi devre dışı bırakır. Canlı değerlendirme kapalıysa, seçenek seçili değildir ve etkin değerlendirmeyi etkinleştirir.  
  
   **Bellek** penceresinin en üstünde araç çubuğunu gizleyebilir veya görüntüleyebilirsiniz. Araç çubuğu gizli olduğu sürece Adres kutusu veya diğer araçlara erişiminiz olmayacaktır.  
  
#### <a name="to-toggle-the-toolbar"></a>Araç çubuğunu değiştirmek için  
  
1. Bir **bellek** penceresine sağ tıklayın.  
  
2. Kısayol menüsünde, **araç çubuğunu göster**' e tıklayın.  
  
     Önceki durumuna bağlı olarak araç çubuğu görünür veya kaybolur.  
  
## <a name="following-a-pointer-through-memory"></a>Bellek üzerinden bir Işaretçiyi takip edin  
 Yerel kod uygulamalarında, ad Kaydet ' i canlı ifadeler olarak kullanabilirsiniz. Örneğin, yığını izlemek için yığın işaretçisini kullanabilirsiniz.  
  
#### <a name="to-follow-a-pointer-through-memory"></a>Bellek üzerinde bir işaretçiyi izlemek için  
  
1. **Bellek** penceresi **adresi** kutusuna bir işaretçi ifadesi yazın. İşaretçi değişkeni geçerli kapsamda olmalıdır. Dile bağlı olarak, bu değere başvuru yapmanız gerekebilir.  
  
2. **ENTER**tuşuna basın.  
  
     Şimdi, **adım**gibi bir yürütme komutu kullandığınızda, işaretçi değiştiğinde görüntülenen bellek adresi otomatik olarak değişecektir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Ayıklayıcıda Verileri Görüntüleme](../debugger/viewing-data-in-the-debugger.md)
