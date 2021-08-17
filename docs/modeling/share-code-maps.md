---
title: Kod eşlemelerini dışarı ve Kaydet
description: kod eşlemelerini bir Visual Studio projesinin parçası olarak, görüntü olarak veya XPS dosyası olarak nasıl kaydedebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d6efe3f860749ac24e35af944122ec8a9d121f6039270117e7eb52eb57fcf6f7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121410949"
---
# <a name="share-code-maps"></a>Kod haritalarını paylaşma

kod eşlemelerini bir Visual Studio projesinin parçası olarak, görüntü olarak veya XPS dosyası olarak kaydedebilirsiniz.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>bir kod haritasını diğer Visual Studio kullanıcılarla paylaşma

Haritayı kaydetmek için **Dosya** menüsünü kullanın.

-veya-

Haritayı belirli projenin bir parçası olarak kaydetmek için harita araç çubuğunda,   >  **Move \<CodeMapName> . dgml**' i içine Share ' ı seçin ve ardından Haritayı kaydetmek istediğiniz projeyi seçin.

![Haritayı başka bir projeye taşıma](../modeling/media/codemapsmovemapmenu.png)

Visual Studio haritayı, diğer Visual Studio Enterprise ve Visual Studio Professional diğer kullanıcılarıyla paylaşabileceğiniz bir *. dgml* dosyası olarak kaydeder.

> [!NOTE]
> Visual Studio Professional kullananlarla bir haritayı paylaşmadan önce, herhangi bir grubu genişlettikten, gizli düğümleri ve çapraz grup bağlantılarını gösterdiğinizden ve başkalarının haritada görmesini istediğiniz silinmiş düğümleri aldığınızdan emin olun. Aksi takdirde, diğer kullanıcıların bu öğeleri görmesi mümkün olmayacaktır.
>
> Modelleme projesinde olan veya bir modelleme projesinden başka bir konuma kopyalanmış olan bir Haritayı kaydettiğinizde aşağıdaki hata ortaya çıkabilir:
>
> " *Dosya adı* proje dizininin dışına kaydedilemez. Bağlantılı öğeler desteklenmez."
>
> Visual Studio hatayı gösterir, ancak kaydedilen sürümü de oluşturur. Hatayı önlemek için Haritayı modelleme projesinin dışında oluşturun. Ardından istediğiniz konuma kaydedebilirsiniz. Yalnızca çözümdeki başka bir konuma dosya kopyalama ve onu kaydetmeye çalışmak başarısızlıkla sonuçlanacaktır.

## <a name="export-a-code-map-as-an-image"></a>Kod haritasını görüntü olarak dışarı aktarma

bir kod haritasını görüntü olarak dışarı aktardığınızda, Microsoft Word veya PowerPoint gibi başka uygulamalara kopyalayabilirsiniz.

1. Kod Haritası araç çubuğunda,   >  **e-postayı görüntü olarak** paylaşma veya **görüntü kopyalama**' yı seçin.

2. Görüntüyü başka bir uygulamaya yapıştırın.

## <a name="export-the-map-as-an-xps-file"></a>Haritayı XPS dosyası olarak dışarı aktarma

Bir kod haritasını XPS dosyası olarak dışa aktardığınızda, bu dosyayı Internet Explorer gibi XML veya XAML görüntüleyicilerinde görebilirsiniz.

1. Kod Haritası araç çubuğunda,   >  **e-postayı taşınabilir XPS olarak** paylaşma veya **Taşınabilir XPS olarak kaydet**' i seçin.

2. Dosyayı kaydetmek istediğiniz yere gidin.

3. Kod eşlemesini adlandırın. **Farklı kaydet türü** kutusunun **XPS dosyaları ( \* . XPS)** olarak ayarlandığından emin olun. **Kaydet**'i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılıkları kod eşlemeleriyle eşleyin](../modeling/map-dependencies-across-your-solutions.md)
