---
title: Hata ayıklayıcıda değişkenler için belleği görüntüleme | Microsoft Docs
ms.custom: ''
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51070e06f684c2e873ded76ec8797ed7587745ff
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348333"
---
# <a name="use-the-memory-windows-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visual Studio hata ayıklayıcısında bellek pencerelerini kullanma (C#, C++, Visual Basic, F #)

Hata ayıklama sırasında, **bellek** penceresi, uygulamanızın kullandığı bellek alanını gösterir.

**İzleme**, **oto**'ler, **Yereller**ve **hızlı izleme** iletişim kutusu gibi hata ayıklayıcı pencereleri, bellekteki belirli konumlarda depolanan değişkenleri gösterir. **Bellek** penceresi size genel resmi gösterir. Bellek görünümü, diğer pencerelerin iyi şekilde göstermeyecek büyük veri parçalarını (örneğin, arabellek veya büyük dizeler) incelemek için uygundur.

**Bellek** penceresi, verileri görüntüleme ile sınırlı değildir. Veri, kod ve atanmamış belleğin rastgele bitleri dahil olmak üzere bellek alanında her şeyi görüntüler.

**Bellek** penceresi, BETIK veya SQL hata ayıklama için kullanılamaz. Bu diller bellek kavramını tanımıyor.

## <a name="open-a-memory-window"></a>Bellek penceresi açma

Diğer hata ayıklayıcı pencereleri gibi, **bellek** pencereleri yalnızca hata ayıklama oturumu sırasında kullanılabilir.

>[!IMPORTANT]
>**Bellek** pencerelerini etkinleştirmek için, **Tools**genel hata ayıklama > araç seçeneklerinde (veya hata ayıklama seçeneklerinde) **Adres düzeyinde hata ayıklamayı etkinleştir** seçeneğinin belirlenmiş olması gerekir  >  **Options** **Debug**  >  **Options** **Debugging**  >  **General**.

**Bellek penceresi açmak için**

1. **Enable address-level debugging** **Tools**  >  **Options** **Debug**  >  **Options** **Hata ayıklama**  >  **genel**> araç seçeneklerinde (veya hata ayıklama seçeneklerinde) Adres düzeyinde hata ayıklamayı etkinleştir ' in seçildiğinden emin olun.

1. Yeşil oku seçerek, **F5**tuşuna basarak **veya hata ayıklama**  >  **başlatma hata ayıklamayı**seçerek hata ayıklamayı başlatın.

2. Windows **belleğini hata ayıkla**altında  >  **Windows**  >  **Memory** **bellek 1**, **bellek 2**, **bellek 3**veya **bellek 4**' ü seçin. (Bazı sürümleri [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yalnızca bir **bellek** penceresi sunar.)

## <a name="move-around-in-the-memory-window"></a>Bellek penceresinde gezinme

Bir bilgisayarın adres alanı büyüktür ve **bellek** penceresinde kaydırma yaparak yerinizi kolayca kaybedebilirsiniz.

Daha yüksek bellek adresleri pencerenin alt kısmında görünür. Daha yüksek bir adres görüntülemek için aşağı kaydırın. Daha düşük bir adres görüntülemek için yukarı kaydırın.

Sürükle ve bırak ' ı kullanarak veya **Adres alanına adresi** girerek, **bellek** penceresinde belirtilen bir adrese anında gidebilirsiniz. **Adres** alanı, alfasayısal adresleri ve adresleri değerlendiren ifadeleri (gibi) kabul eder `e.User.NonroamableId` .

**Adres** alanındaki bir ifadenin anında yeniden değerlendirilmesini zorlamak için, yuvarlatılmış ok simgesini **otomatik olarak** yeniden değerlendir simgesini seçin.

Varsayılan olarak, **bellek** penceresi **Adres** ifadelerini, uygulama çalışırken yeniden değerlendirilen canlı ifadeler olarak değerlendirir. Canlı ifadeler, örneğin bir işaretçi değişkeni tarafından dokundukları belleği görüntülemek için yararlı olabilir.

**Bir bellek konumuna geçmek için sürükle ve bırak öğesini kullanmak için:**

1. Herhangi bir hata ayıklayıcı penceresinde, bir bellek adresi veya bir bellek adresi içeren bir işaretçi değişkeni seçin.

2. **Bellek** penceresinde adresi veya işaretçiyi sürükleyip bırakın. Bu adres daha sonra **Adres** alanında görünür ve **bellek** penceresi bu adresi en üstte görüntüleyecek şekilde ayarlar.

**Adres alanına girerek bir bellek konumuna geçmek için:**

- **Adres alanına adres** veya ifade yazın veya yapıştırın, **ENTER**tuşuna basın veya **Adres** alanındaki açılır listeden seçin. **Bellek** penceresi, bu adresi en üstte görüntüleyecek şekilde ayarlar.

## <a name="customize-the-memory-window"></a>Bellek penceresini özelleştirme

Varsayılan olarak, bellek içerikleri onaltılık biçimde 1 baytlık tamsayılar olarak görünür ve pencere genişliği gösterilen sütun sayısını belirler. **Bellek** penceresinin bellek içeriğini gösterir biçimini özelleştirebilirsiniz.

**Bellek içeriğinin biçimini değiştirmek için:**

- **Bellek** penceresinde sağ tıklayın ve bağlam menüsünden istediğiniz biçimleri seçin.

**Bellek penceresindeki sütun sayısını değiştirmek için:**

- **Sütunlar** alanının yanındaki aşağı açılan oku seçin ve görüntülenecek sütun sayısını seçin veya pencere genişliğine göre otomatik ayarlama için **Otomatik** ' i seçin.

Uygulamanızın çalıştırıldığı sürece **bellek** penceresinin içeriğinin değiştirilmesini istemiyorsanız, canlı ifade değerlendirmesini devre dışı bırakabilirsiniz.

**Canlı değerlendirmeyi değiştirmek için:**

- **Bellek** penceresinde sağ tıklayın ve bağlam menüsünde **otomatik olarak** yeniden değerlendir ' i seçin.

  >[!NOTE]
  >Canlı ifade değerlendirmesi bir geçişli, varsayılan olarak açık olduğundan yeniden değerlendirilen ' ı seçtiğinizde **otomatik olarak** devre dışı bırakır. Yeniden **değerlendirmeyi otomatik olarak** seçme seçeneği tekrar açılır.

**Bellek** penceresinin en üstünde araç çubuğunu gizleyebilir veya görüntüleyebilirsiniz. Araç çubuğu gizli olduğunda **Adres** alanına veya diğer araçlara erişiminiz olmayacaktır.

**Araç çubuğunun görüntülenmesini değiştirmek için:**

- **Bellek** penceresinde sağ tıklayın ve bağlam menüsünde **araç çubuğunu göster** ' i seçin. Önceki durumuna bağlı olarak araç çubuğu görünür veya kaybolur.

## <a name="follow-a-pointer-through-memory"></a>Bellek üzerinde bir işaretçiyi takip edin

Yerel kod uygulamalarında, YAZMAÇ adlarını canlı ifadeler olarak kullanabilirsiniz. Örneğin, yığını izlemek için yığın işaretçisini kullanabilirsiniz.

**Bellek üzerinden bir işaretçiyi izlemek için:**

1. **Bellek** penceresi **adresi** alanında, geçerli kapsamda olan bir işaretçi ifadesi girin. Dile bağlı olarak, bu değere başvuru yapmanız gerekebilir.

2. **Enter**'a basın.

   **Adım**gibi bir hata ayıklama komutu kullandığınızda, **Adres** alanında ve **bellek** penceresinin en üstünde görünen bellek adresi, işaretçi değiştiğinde otomatik olarak değişir.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)