---
title: Geçmiş hata ayıklama | Microsoft Docs
description: Bir uygulamada, geriye doğru ilerleyerek ve daha ileri doğru hareket ederek durumunu inceleyerek sorun giderin. IntelliTrace bu yetenek için bilgileri toplar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38166f777153206ad4b862ac473226aecdff4147
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398551"
---
# <a name="historical-debugging-c-visual-basic-c"></a>Geçmiş hata ayıklama (C#, Visual Basic, C++)

Geçmiş hata ayıklama, IntelliTrace tarafından toplanan bilgilere bağlı bir hata ayıklama modudur. Geri taşımanızı ve uygulamanızın yürütülmesini ve durumunu incelemenizi sağlar.

 IntelliTrace 'i Visual Studio Enterprise sürümünde (ancak Professional veya Community sürümlerinde kullanamazsınız) kullanabilirsiniz.

## <a name="why-use-historical-debugging"></a>Geçmiş hata ayıklama neden kullanılmalıdır?

 Hataları bulmak için kesme noktalarının ayarlanması, bir veya daha fazla isabetsizlik olabilir. Kodunuzda hatanın olması şüpheli olan yere bir kesme noktası, sonra da uygulamayı hata ayıklayıcısında çalıştırmanız ve yürütme sonlarının hata kaynağını açığa çıkarması için gereken yerde bir kesme noktası ayarlayın. Aksi takdirde, bir kesme noktasını kodda başka bir yerde ayarlamayı ve hata ayıklayıcıyı yeniden çalıştırmayı denemeniz gerekir.

 ![kesme noktası ayarlama](../debugger/media/breakpointprocesa.png "BreakpointProcesa")

 Uygulama içinde dolaşırken IntelliTrace ve geçmiş hata ayıklamayı kullanabilir ve kesme noktaları ayarlamak zorunda kalmadan durumunu (çağrı yığını ve yerel değişkenler) inceleyebilir, hata ayıklamayı yeniden başlatabilir ve test adımlarını tekrarlayabilirsiniz. Bu, özellikle de hata, yürütülmesi uzun süren bir test senaryosunda derin olduğunda sizi çok zaman kaydedebilir.

## <a name="how-do-i-start-using-historical-debugging"></a>Geçmiş hata ayıklamayı kullanmaya başlamak Nasıl yaparım? mı?

IntelliTrace varsayılan olarak açık. Yapmanız gereken tek şey, hangi olayların ve işlev çağrılarının size ilgilendiği ve tam uygulama durumlarınızın anlık görüntülerini görüntülemek isteyip istemediğiniz konusunda karar verendir. Ne aramak istediğinizi tanımlama hakkında daha fazla bilgi için bkz. [IntelliTrace Özellikleri](../debugger/intellitrace-features.md). Özellik desteği dile ve uygulama türüne göre farklılık gösterir.

- Geçmiş hata ayıklama ile anlık görüntüleri görüntülemek için bkz. [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md)
- Değişkenleri İnceleme ve koda gitme hakkında bilgi edinmek için bkz. [geçmiş hata ayıklama ile uygulamanızı İnceleme](../debugger/historical-debugging-inspect-app.md)
- IntelliTrace olayları ile hata ayıklama hakkında daha fazla bilgi edinmek için bkz. [Izlenecek yol: IntelliTrace kullanma](../debugger/walkthrough-using-intellitrace.md).