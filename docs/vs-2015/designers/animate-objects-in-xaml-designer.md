---
title: XAML Tasarımcısı nesnelere animasyon ekleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ea2fdf1f47385a9be26fa65a93b9104b2d864079
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658018"
---
# <a name="animate-objects-in-xaml-designer"></a>XAML Tasarımcısı’nda nesnelere animasyon ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Nesneleri taşımak veya onları dışarı veya dışarı soluklaştırmak için kısa animasyonlar oluşturabilirsiniz.

 Başlamak için bir *görsel taslak*oluşturun. Film şeridi bir veya daha fazla *zaman çizelgesi*içerir. Özellik değişikliklerini işaretlemek için zaman çizelgesinde *ana kareleri* ayarlayın. Daha sonra, animasyonu çalıştırdığınızda, Blend özelliği belirlenen süre boyunca özellik değişikliklerini enterpolasyonlar. Sonuç kesintisiz bir geçiştir. Nesneye ait olan herhangi bir özelliğe, hatta görsel olmayan özelliklere animasyon uygulayabilirsiniz.

 Aşağıdaki çizimde, **MoveUp**adlı bir görsel taslak gösterilmektedir. Zaman çizelgesi, bir dikdörtgenin X ve Y konumunu işaretleyen ana kareleri içerir. Bu animasyon çalıştırıldığında, dikdörtgen bir konumdan diğerine doğru gider.

 ![](../designers/media/982f031a-74a3-414a-abc2-a0f41a741075.png "982f031a-74a3-414a-abc2-a0f41a741075")

 Bu videoları izleyerek animasyon oluşturmayı öğrenin.

|Kısa bir video izleyin:|Şunları yapmayı öğrenin:|
|--------------------------|-------------------|
|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [zaman çizelgeleri oluşturma](http://www.popscreen.com/v/6A4eF/Microsoft-Expression-Blend-Creating-Timelines)|Zaman çizelgesi oluşturun ve zaman çizelgesinde nesnelerle çalışın.|
|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [anahtar kareler ekleme ve animasyonu yineleme](http://www.popscreen.com/v/6A4fi/Microsoft-Expression-Blend-Adding-Keyframes-and-Repeating-an-Animation)|Her bir ana karede anahtar kareler ekleyin ve özellikleri ayarlayın. Ardından, animasyonu çalıştırın ve nesneler arasında sorunsuzca geçiş yapın.|
|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [etkileşimli için olay tetikleyicileri ekleme](http://www.popscreen.com/v/6A4e4/Microsoft-Expression-Blend-Adding-Event-Triggers-for-Interactivity)|Bir olay gerçekleştiğinde bir animasyon başlatın. Örneğin, pencere yüklenirken bir tane başlatın.|
|![Yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [renk animasyonu](http://www.popscreen.com/v/6A4gv/Microsoft-Expression-Blend-Animating-Colors)|Bir nesnenin rengini değiştirmek için animasyon kullanın.|
|![Yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [hareket yollarını oluşturma ve değiştirme](http://www.popscreen.com/v/6A4fX/Microsoft-Expression-Blend-Creating-and-Modifying-Motion-Paths)|Nesneleri bir yol üzerinde canlandırın.|
|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [kolaylığı ana kareleri](http://www.popscreen.com/v/6A4dM/Microsoft-Expression-Blend-Easing-Keyframes)|Bir animasyonun başlangıcında (*üzerinde hareket*eden) veya ekranın sonuna yakın (*hareket hızı*) yakınında bir animasyonu hızlandıramaz veya yavaşlatır.|
|![Yüklü Özellikleri Yapılandır](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [düğmesine animasyon ekleme](http://www.popscreen.com/v/6A4fK/Microsoft-Expression-Blend-Animating-a-Button)|Kullanıcı ona işaret eden bir düğme üzerinde görünen ilginç etkileri oluşturun.|
|![Yüklü özellikleri yapılandırma](../designers/media/bldadminconsoleinitialconfigicon.PNG "Bldadminconsoleınitialconfigıcon") [animasyon oluşturma ve kolaylaştırıcı ile çalışma](https://www.youtube.com/watch?v=mAJXYrwxGYo)|Bir Kullanıcı Hesaplayıcı görüntüsündeki bir düğmeye bastığında görüntülenen etkilere animasyon ekleyin.|

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio için Blend’i kullanarak kullanıcı arabirimi oluşturma](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)
