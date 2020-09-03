---
title: İş Akışı Tasarımcısı- &lt; T &gt; etkinlik tasarımcısını Değiştir
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.ModelItemKeyValuePair.UI
- System.Activities.Statements.Switch`1.UI
ms.assetid: 18a6c96e-49a9-4356-ab61-fbd7e3ab44bb
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7430dec75e898a6695b146ce50076b8f57ed9d3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88711618"
---
# <a name="switcht-activity-designer"></a>Switch\<T> Etkinlik Tasarımcısı

<xref:System.Activities.Statements.Switch%601>Etkinlik belirtilen bir ifadeyi değerlendirir ve aktiviteyi, ilişkili anahtarı değerlendirmeden elde edilen değerle eşleşen bir etkinlik koleksiyonundan yürütür.

**Anahtar<T \> ** etkinlik Tasarımcısı iş akışı Tasarımcısı bir etkinlik oluşturmak ve yapılandırmak için kullanılır <xref:System.Activities.Statements.Switch%601> .

## <a name="the-switchtactivity"></a>Switch \<T> etkinliği

Bir <xref:System.Activities.Statements.Switch%601> etkinlik bir <xref:System.Activities.Statements.Switch%601.Expression%2A> ve sözlüğünü içerir <xref:System.Activities.Statements.Switch%601.Cases%2A> . Sözlükteki her bir durum, bir *anahtar* ve karşılık gelen *değeri*olarak hizmet veren bir etkinlik içeren bir çiftin oluşur. <xref:System.Activities.Statements.Switch%601>Etkinliği değerlendirir <xref:System.Activities.Statements.Switch%601.Expression%2A> ve anahtarların her birine karşı karşılaştırır. Bir eşleşme bulunursa ilgili etkinlik yürütülür. Sözlük anahtarlarının, sözlüğün eşitlik karşılaştırıcısı tarafından tanımlanan eşitlik türüne göre benzersiz olması gerektiğinden yalnızca bir eşleşme mümkündür. Eşleşme bulunmazsa <xref:System.Activities.Statements.Switch%601.Default%2A> etkinlik yürütülür.

## <a name="how-to-use-the-switcht-activity-designer"></a>Switch \<T> etkinlik tasarımcısını kullanma

**Araç kutusunun** **Denetim akışı** kategorisindeki ** \<T> Switch** etkinlik tasarımcısına erişin. İş Akışı Tasarımcısı, kullanıcının Etkinlikte kullanılan genel tür *T* 'yi belirtmesini sağlamak Için **türleri Seç** iletişim kutusunu görüntüler <xref:System.Activities.Statements.Switch%601> . Varsayılan değer **Int32**'dir. Genel tür *t* seçildikten sonra, iş akışı tasarımcısına bir **anahtar<T \> ** Designer eklenir.

**Anahtar<T \> ** Designer 'ın özellikleri aşağıda verilmiştir. Bu özelliklerin tümü, özellik kılavuzunda düzenlenebilir. Bunlardan bazıları tasarımcı yüzeyi üzerinde de düzenlenebilir.

Aşağıdaki tabloda en yararlı <xref:System.Activities.Statements.Switch%601> Özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|Yanlış|Etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.Switch%601> . Varsayılan değer<Int32 ' dir \> . Değer, **Özellikler** penceresinde veya doğrudan tasarımcı üstbilgisinde düzenlenebilir.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Switch%601.Expression%2A>|Doğru|Hangi durumun yürütüleceğini öğrenmek için servis talepleri koleksiyonundaki anahtarlarla karşılaştırmak için kullanılan ifadeyi belirtir.|
|<xref:System.Activities.Statements.Switch%601.Default%2A>||Hiçbir eşleşme bulunmazsa yürütülen etkinliği belirtir. Etkinliğin bırakılbileceği **varsayılan** kutuyu açmak için tasarımcıda **etkinlik Ekle** düğmesine tıklayın.|
|<xref:System.Activities.Statements.Switch%601.Cases%2A>||Değerlendirilecek çalışmaları belirtir. Bir durum eklemek için, **anahtar \<T> ** Tasarımcısı ' nın alt kısmındaki **yeni durum Ekle** düğmesine tıklayın. Düğme, bir TextBox olarak değişir (anahtar eklenirken seçili genel tür \<T> dize veya sabit listesi ise Birleşik giriş kutusu). **Case değer** kutusuna bir anahtar eklendikten sonra, Case alanı genişler ve bir etkinlik, durum için yürütme mantığını tanımlamak üzere ipucu metninde "etkinliği buraya bırak" olarak da çalıştırılabilir.|

Büyük/küçük harf anahtarları yinelenmediğinden, birden çok durum eklenebilir. Aksi halde, belirtilen Case anahtarının zaten var olduğunu ve farklı bir anahtar seçmeniz gerektiğini bildiren bir hata iletişim kutusu görüntülenir. **Anahtar \<T> ** tasarımcısında, tek seferde yalnızca bir Case alanı genişletilmiş görünümde olabilir. Bir Case alanı daraltılmış görünümdayken, büyük/küçük harfe tıklamak onu genişletir. Daraltılan bir durumda tasarımcı, etkinliğin görünen adını, varsa sağ taraftaki büyük küçük harf olarak gösterir. Aksi takdirde, bu durum, tıkladığınızda ve bir etkinlik eklemenize olanak varsa, bu durumu genişleten **bir etkinlik Ekle** düğmesi gösterir.

Mevcut durumda olan anahtara tıkladığınızda, bir etiketten anahtar TextBox olarak değişir. böylece, Case anahtarını düzenleyebilmenizi sağlayabilirsiniz.

Bir servis talebi silmenin 2 yolu vardır:

- Büyük/küçük harf ' i seçin ve silin.

- Büyük/küçük harf ' i seçin, sağ tıklayarak bağlam menüsünü görüntüleyin ve **Sil**' i seçin.

Silmek için büyük/küçük harf ' i seçmeniz gerektiğini unutmayın. Etkinlik yalnızca bir servis talebi içinde seçilip silindiğinde etkinlik yalnızca durum değil olarak silinir.

## <a name="see-also"></a>Ayrıca bkz.

- [Denetim akışı](../workflow-designer/control-flow-activity-designers.md)
