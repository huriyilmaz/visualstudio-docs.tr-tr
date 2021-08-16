---
title: XAML Tasarımcısı’nda nesnelere animasyon ekleme
titleSuffix: Blend for Visual Studio
description: Visual Studio için Blend'de bir nesneye animasyon Visual Studio için Blend zaman çizelgesi ve ana çerçeveler ile görsel çizim kullanarak bir animasyon XAML Tasarımcısı.
ms.custom: SEO-VS-2020
ms.date: 07/31/2019
ms.topic: how-to
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: da206cedbe2cf14be1fc6bcd2d8f1dd1cd154524767ed9b33ddb69e392599053
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121393472"
---
# <a name="animate-objects-in-xaml-designer"></a>XAML Tasarımcısı’nda nesnelere animasyon ekleme

Visual Studio için Blend nesneleri hareket ettiren veya solduran kısa animasyonları kolayca oluşturmanıza olanak sağlar.

Animasyon oluşturmak için bir görsel görseli *oluşturmanız gerekir.* Bir storyboard bir veya daha fazla zaman *çizelgesi içerir.* Özellik *değişikliklerini işaretlemek* için zaman çizelgesinde ana kareler ayarlayın. Ardından animasyonu çalıştırarak Visual Studio için Blend zaman içinde özellik değişikliklerini ilişkilendirmeniz gerekir. Sonuç sorunsuz bir geçiştir. Görsel olmayan özellikler bile bir nesneye ait olan herhangi bir özel nesneye animasyon sızabilirsiniz.

Aşağıdaki görüntülerDeleta1 adlı **bir görsel şeridi gösterir.** Zaman çizelgesi, dikdörtgenin X ve Y konumunu işaret alan ana kareler içerir. Bu animasyon çalıştır geldiğinde dikdörtgen bir konumdan diğerine sorunsuz bir şekilde taşınır.

![Visual Studio için Blend'da animasyon için görsel Visual Studio için Blend](media/storyboard-timeline.png)

## <a name="create-an-animation"></a>Animasyon oluşturma

1. Bir storyboard oluşturmak için, Nesneler ve Zaman Çizelgesi **penceresindeKimlik** Nesneler ve Zaman Çizelgesi düğmesini **seçin.** 

   ![Visual Studio için Blend'a bir storyboard ekleme](media/new-storyboard.png)

2. Storyboard **Kaynağı Oluştur iletişim** kutusunda, storyboard için bir ad girin.

3. Tasarım görünümü'daki Varlıklar panelinden sayfanın sol alt tarafına bir dikdörtgen ekleyin. 

   ![XAML Tasarımcısı'nin Varlıklar panelindeki dikdörtgen](media/add-rectangle.PNG)

4. Aşağıdaki **Nesneler ve Zaman Çizelgesi,** sarı saat işaretçisini **3 saniyeye** hareket ettirin.

   ![Zaman çizelgesinde saat göstergesi](media/timeline-indicator.PNG)

5. Sayfanın Tasarım görünümü dikdörtgeni sayfanın sağ tarafına sürükleyin.

6. **Dikdörtgenin** sol taraftan sayfanın sağ tarafına taşınmalarını izlemek için Oynat'a basın.

Dikdörtgende zaman içinde farklı noktalarda yapılan diğer değişikliklerle dolaşarak. Örneğin, dolgu rengini değiştirebilir veya yönlendirmeyi ters çevirebilir Özellikler penceresi.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../xaml-tools/creating-a-ui-by-using-blend-for-visual-studio.md)
