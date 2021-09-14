---
title: Kod haritalarını dışarı aktarma ve kaydetme
description: Kod haritalarını bir Visual Studio projesinin parçası olarak, görüntü olarak veya XPS dosyası olarak kaydetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 05/16/2018
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 2d9e89ed659969074553e366f0e35581c319801c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637433"
---
# <a name="share-code-maps"></a>Kod haritalarını paylaşma

Kod haritalarını bir Visual Studio parçası olarak, görüntü olarak veya XPS dosyası olarak kaydedebilirsiniz.

## <a name="share-a-code-map-with-other-visual-studio-users"></a>Kod haritasını diğer kullanıcılarla Visual Studio paylaşma

Haritayı **kaydetmek** için Dosya menüsünü kullanın.

-veya-

Haritayı belirli bir projenin parçası olarak kaydetmek için harita araç çubuğunda  >  **Taşı \<CodeMapName> .dgml** dosyasını içine paylaş'ı seçin ve ardından haritayı kaydetmek istediğiniz projeyi seçin.

![Haritayı başka bir projeye taşıma](../modeling/media/codemapsmovemapmenu.png)

Visual Studio, haritayı diğer kullanıcı ve kullanıcı kullanıcılarını paylaşabilirsiniz *bir .dgml* Visual Studio Enterprise Visual Studio Professional.

> [!NOTE]
> Haritayı Visual Studio Professional kullananlarla paylaşmadan önce grupları genişletmeyi, gizli düğümleri ve çapraz grup bağlantılarını göstermeyi ve başkalarının haritanıza göstermesini istediğiniz silinmiş düğümleri almaya emin olun. Aksi takdirde, diğer kullanıcıların bu öğeleri görmesi mümkün olmayacaktır.
>
> Bir modelleme projesinde yer alan veya bir modelleme projesinden başka bir konuma kopyalanan bir haritayı kaydeden aşağıdaki hata oluşabilir:
>
> *"fileName proje dizini* dışında kaydedilemeyen. Bağlantılı öğeler desteklenmez."
>
> Visual Studio hatayı gösterir, ancak kaydedilen sürümü de oluşturur. Hatayı önlemek için haritayı modelleme projesinin dışında oluşturun. Ardından istediğiniz konuma kaydedebilirsiniz. Yalnızca çözümdeki başka bir konuma dosya kopyalama ve onu kaydetmeye çalışmak başarısızlıkla sonuçlanacaktır.

## <a name="export-a-code-map-as-an-image"></a>Kod haritasını görüntü olarak dışarı aktarma

Bir kod haritasını görüntü olarak dışarı aktararak kod eşlemesi gibi diğer uygulamalara Microsoft Word PowerPoint.

1. Kod haritası araç çubuğunda E-postayı Görüntü **Olarak Paylaş veya** Görüntü  >  **Kopyala'ya** **tıklayın.**

2. Görüntüyü başka bir uygulamaya yapıştırın.

## <a name="export-the-map-as-an-xps-file"></a>Haritayı XPS dosyası olarak dışarı aktarma

Bir kod haritasını XPS dosyası olarak dışarı aktararak XML veya XAML görüntüleyicilerde Internet Explorer.

1. Kod haritası araç çubuğunda, E-postayı Taşınabilir XPS Olarak Paylaş veya Taşınabilir   >  **XPS** **Olarak Kaydet'i seçin.**

2. Dosyayı kaydetmek istediğiniz yere gidin.

3. Kod eşlemesi olarak ad girin. Farklı kaydet türü **kutusunun XPS dosyaları** **( \* .xps) olarak ayarlanmış olduğundan emin olun.** **Kaydet**'i seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Bağımlılıkları kod eşlemeleriyle eşleme](../modeling/map-dependencies-across-your-solutions.md)
