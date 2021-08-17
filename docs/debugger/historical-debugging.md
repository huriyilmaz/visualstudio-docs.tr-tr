---
title: Geçmiş Hata Ayıklama | Microsoft Docs
description: Bir uygulamanın yürütmesi boyunca geri ve ileri doğru ilerlerken durumunu incelerken uygulamanın sorunlarını giderin. Intellitrace bu özellik için bilgileri toplar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 0d3198e5fb784cac999097167ef2499004823781
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122074156"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Geçmiş hata ayıklama (C#, Visual Basic, C++)

Geçmiş hata ayıklama, IntelliTrace tarafından toplanan bilgilere bağlı olan bir hata ayıklama modudur. Bu sayede, uygulamanın yürütülmesiyle geriye ve ileriye doğru hareket edebilir ve durumunu incelersiniz.

 IntelliTrace'i Visual Studio Enterprise sürümlerinde kullanabilirsiniz (ancak Professional veya Community değil).

## <a name="why-use-historical-debugging"></a>Neden geçmiş hata ayıklamayı kullanasınız?

 Hataları bulmak için kesme noktaları ayarlama, oldukça isabetli veya isabet isabetli olabilir. Kodda hatadan şüphelenilen yere yakın bir kesme noktası ayarlayın, sonra uygulamayı hata ayıklayıcısında çalıştırın ve kesme noktanıza isabet etmek ve yürütmenin kesme noktalarında hatanın kaynağını ortaya çıkarabilirsiniz. Ayarlanmazsa, kodun başka bir yerine kesme noktası ayarlamayı denemeniz ve hata ayıklayıcıyı yeniden çalıştırmanız ve sorunu bulana kadar test adımlarınızı tekrar tekrar yürütmeniz gerekir.

 ![kesme noktası ayarlama](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 Kesme noktaları ayarlamak, hata ayıklamayı yeniden başlatmak ve test adımlarını yinelemek zorunda kalmadan uygulama içinde dolaşarak durumunu (çağrı yığını ve yerel değişkenler) incelemek için IntelliTrace ve geçmiş hata ayıklamayı kullanabilirsiniz. Bu, özellikle hatanın yürütülme süresi uzun olan bir test senaryosunun derinlerinde yer alıyorsa çok fazla zaman tasarrufu sağlar.

## <a name="how-do-i-start-using-historical-debugging"></a>Nasıl yaparım? hata ayıklamayı kullanmaya başlayabilir misiniz?

IntelliTrace varsayılan olarak açıktır. Tek gereken, hangi olayların ve işlev çağrılarının ilginizi çekmek istediğinize ve tam uygulama durumu anlık görüntülerinizi görüntülemek isteyip istediğinize karar vermektir. Neleri görmek istediğiniz hakkında daha fazla bilgi için bkz. [IntelliTrace Özellikleri.](../debugger/intellitrace-features.md) Özellik desteği dile ve uygulama türüne göre değişir.

- Geçmiş hata ayıklama ile anlık görüntüleri görüntülemek için [bkz. IntelliTrace kullanarak önceki uygulama eyaletlerini inceleme](../debugger/view-historical-application-state.md)
- Değişkenleri incelemeyi ve kodda gezinmeyi öğrenmek için [bkz. Geçmiş hata ayıklama ile uygulamanızı inceleme](../debugger/historical-debugging-inspect-app.md)
- IntelliTrace olaylarıyla hata ayıklama hakkında daha fazla bilgi edinmek için [bkz. Walkthrough: Using IntelliTrace](../debugger/walkthrough-using-intellitrace.md).