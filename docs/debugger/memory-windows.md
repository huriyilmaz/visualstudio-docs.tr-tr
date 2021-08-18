---
title: Hata ayıklayıcısında değişkenlerin belleğini | Microsoft Docs
description: Hata ayıklarken, uygulamanın hangi bellek alanı olduğunu görmek için Bellek pencerelerini kullanmayı öğrenin. Diğer pencereler değişkenleri ve bellekte nerede olduklarını gösterir.
ms.custom: SEO-VS-2020
ms.date: 10/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.memory
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Memory window
- strings [Visual Studio], viewing
- debugger [Visual Studio], Memory window
- memory [Visual Studio], debugging
- debugging [Visual Studio], Memory window
- buffers, viewing
ms.assetid: 7f7a0439-10e4-4966-bb2d-51f04cda4fe2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 8a725ced36f886054094cc0ce97da34a1a74d3da
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090726"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio hata ayıklayıcısında Bellek pencerelerini kullanma (C#, C++, Visual Basic, F#)

Hata ayıklama sırasında **Bellek penceresinde,** uygulamanın kullanmakta olduğu bellek alanı gösterilir.

İzleme, Otomatikler, Yereller **ve** **QuickWatch** iletişim kutusu gibi hata ayıklayıcı pencereleri, belirli bellek konumlarında depolanan değişkenleri gösterir. Bellek **penceresinde** genel resim gösterilir. Bellek görünümü, diğer pencerelerde iyi görüntülenmeen büyük veri parçalarını (arabellekler veya büyük dizeler gibi) incelemeniz için kullanışlıdır.

Bellek **penceresi** verileri görüntülemekle sınırlı değildir. Bellek alanı içinde veriler, kod ve atanmamış bellekte rastgele çöp bitleri dahil olmak üzere her şeyi görüntüler.

Bellek **penceresi** betik veya hata ayıklama SQL kullanılamaz. Bu diller bellek kavramını tanımaz.

## <a name="open-a-memory-window"></a>Bellek penceresi açma

Diğer hata ayıklayıcı pencerelerde **olduğu gibi Bellek** pencereleri de yalnızca bir hata ayıklama oturumu sırasında kullanılabilir.

>[!IMPORTANT]
>Bellek pencerelerini **etkinleştirmek** **için,** Araç Seçenekleri (veya Hata Ayıklama Seçenekleri) menüsünde Adres düzeyinde hata ayıklamayı etkinleştir seçeneği seçilmelidir ve  >   > Ayıklama   >   **Genel'e**  >  **tıklayın.**

**Bir Bellek penceresi açmak için**

1. Genel Hata **Ayıklama için Araçlar Seçenekleri (veya** Hata Ayıklama Seçenekleri) içinde Adres düzeyinde hata   >     >  ayıklamayı etkinleştir > **emin**  >  **olun.**

1. Yeşil oku seçerek, **F5** tuşuna basarak veya Hata AyıklamaYı Başlat'ı **seçerek**  >  **hata ayıklamaya başlama.**

2. Bellekte **Hata**  >  **Windows**  >  **altında** Bellek **1, Bellek 2**, **Bellek 3** veya Bellek **4'ü seçin.**  (Bazı sürümleri yalnızca [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir Bellek **penceresi** sağlar.)

## <a name="move-around-in-the-memory-window"></a>Bellek penceresinde hareket etme

Bir bilgisayarın adres alanı büyük ve Bellek penceresinde kaydırarak yerlerinizi kolayca **kaybedebilirsiniz.**

Pencerenin alt kısmında daha yüksek bellek adresleri görüntülenir. Daha yüksek bir adresi görüntülemek için ekranı aşağı kaydırın. Daha düşük bir adresi görüntülemek için yukarı kaydırın.

Bellek penceresinde sürükle ve bırak kullanarak  veya adresi Adres alanına girerek anında belirtilen adrese **gidebilirsiniz.** Adres **alanı** alfasayısal adresleri ve gibi adresleri değerlendiren ifadeleri kabul `e.User.NonroamableId` eder.

Adres alanında bir ifadenin hemen yeniden değerlendirilmesini zorlamak **için** yuvarlanmış oku Otomatik olarak Yeniden **Değerlendir simgesini** seçin.

Varsayılan olarak, **Bellek** penceresi Adres **ifadelerini** uygulama çalıştırıldık yeniden değerlendirilen canlı ifadeler olarak değerlendirir. Örneğin, bir işaretçi değişkeni tarafından dokunan belleği görüntülemek için canlı ifadeler yararlı olabilir.

**Bir bellek konuma taşımak için sürükleyip bırakma kullanmak için:**

1. Herhangi bir hata ayıklayıcısı penceresinde bir bellek adresi veya bellek adresi içeren bir işaretçi değişkeni seçin.

2. Adresi veya işaretçiyi Bellek penceresine **sürükleyip** bırakın. Bu adres daha sonra **Adres alanında** görünür ve **Bellek** penceresi bu adresi en üstte görüntülemek için ayarlanır.

**Adres alanına girerek bir bellek konuma taşımak için:**

- Adres alanına adresi veya ifadeyi yazın veya **yapıştırın** ve **Enter** tuşuna basın veya Adres alanında açılan listesinden **seçin.** Bellek **penceresi,** bu adresi en üstte görüntülemek için ayarlanır.

## <a name="customize-the-memory-window"></a>Bellek penceresini özelleştirme

Varsayılan olarak, bellek içeriği onaltılık biçimde 1 bayt tamsayı olarak görünür ve gösterilen sütun sayısını pencere genişliği belirler. Bellek penceresinin bellek içeriğini **görüntüleme** yolunu özelleştirebilirsiniz.

**Bellek içeriğinin biçimini değiştirmek için:**

- Bellek penceresine **sağ** tıklayın ve bağlam menüsünden istediğiniz biçimleri seçin.

**Bellek penceresindeki sütun sayısını değiştirmek için:**

- Sütunlar alanı'nın yanındaki  açılan oku seçin ve görüntülemek istediğiniz sütun  sayısını seçin veya pencere genişliğine göre otomatik ayarlama için Otomatik'i seçin.

Uygulamanız çalışırken Bellek **penceresinin** içeriğinin değişmesini istemiyorsanız canlı ifade değerlendirmesini kapatabilirsiniz.

**Canlı değerlendirmeyi iki durumlu olarak yapmak için:**

- Bellek penceresine sağ **tıklayın** ve bağlam **menüsünden Otomatik olarak Yeniden Değerlendir'i** seçin.

  >[!NOTE]
  >Canlı ifade değerlendirmesi bir iki durumlu düğmedir ve varsayılan olarak açıktır, bu nedenle Yeniden **Değerlendir'i** seçmek otomatik olarak bunu kapattır. Yeniden Değerlendir **seçeneğinin Otomatik olarak yeniden** seçerek yeniden açılır.

Araç çubuğunu Bellek penceresinin üst kısmında gizleyebilirsiniz veya **görüntüleyebilirsiniz.** Araç çubuğu gizli olduğunda **Adres alanına** veya diğer araçlara erişemezsiniz.

**Araç çubuğu görüntüsüne geçiş yapmak için:**

- Bellek penceresine sağ **tıklayın ve** bağlam menüsünde Araç **Çubuğunu Göster'i** seçin. Araç çubuğu, önceki durumuna bağlı olarak görünür veya kaybolur.

## <a name="follow-a-pointer-through-memory"></a>Bellekte işaretçiyi izleme

Yerel kod uygulamalarındaki kayıt adlarını canlı ifade olarak kullanabilirsiniz. Örneğin, yığını takip etmek için yığın işaretçisini kullanabilirsiniz.

**Bellekte bir işaretçiyi takip etmek için:**

1. Bellek **penceresi** Adres **alanına** geçerli kapsamda bir işaretçi ifadesi girin. Dile bağlı olarak, dil için başvuruyu geri alamanıza gerek olabilir.

2.  **Enter** tuşuna basın.

   Adım gibi bir hata ayıklama komutu kullanırken, Adres  alanında ve Bellek penceresinin üst kısmında görüntülenen bellek adresi işaretçi değişti olarak otomatik olarak değişir.  

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)