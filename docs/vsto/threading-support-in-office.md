---
title: Office'de iş parçacığı Office
description: İş parçacığı oluşturma, iş parçacığı Microsoft Office modelde de destekler. İş Office modeli iş parçacığı güvenli değildir, ancak bir iş parçacığı çözümünde birden çok iş parçacığıyla Office olabilir.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 0313a6c0b263cfb47cbde84524682db446fc29050fa42b639e2fed407d33b9ee
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423819"
---
# <a name="threading-support-in-office"></a>Office'de iş parçacığı Office
  Bu makalede, iş parçacığı oluşturmanın iş parçacığı oluşturma nesne modelinde Microsoft Office bilgiler sağlar. İş Office modeli iş parçacığı güvenli değildir, ancak bir iş parçacığı çözümünde birden çok iş parçacığıyla Office mümkündür. Office, Bileşen Nesne Modeli (COM) sunucularıdır. COM, istemcilerin rastgele iş parçacıklarında COM sunucularını çağırmalarına olanak sağlar. İş parçacığı güvenli değil COM sunucuları için, COM eş zamanlı çağrıları seri hale getirme mekanizması sağlar, böylece herhangi bir anda sunucuda yalnızca bir mantıksal iş parçacığı yürütülür. Bu mekanizma, tek iş parçacıklı zincir (STA) modeli olarak bilinir. Çağrılar seri hale getirildikleri için, sunucu meşgulken veya arka plan iş parçacığında diğer çağrıları iş alırken çağıranlar zaman zaman engellenmiş olabilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Birden çok iş parçacığı kullanırken gereken bilgi
 Birden çok iş parçacığıyla çalışmak için, çoklu iş parçacığının aşağıdaki yönleri hakkında en azından temel bilgilere sahipsiniz:

- Windows Apı 'leri

- COM çok iş parçacıklı kavramları

- Eşzamanlılık

- Eşitleme

- Hazırlama

  Çoklu iş parçacığı hakkında genel bilgi için bkz. [Yönetilen iş parçacığı.](/dotnet/standard/threading/)

  Office STA'da çalışır. Bunun etkilerini anlamak, birden çok iş parçacığının birden çok iş parçacığını birden çok iş parçacığıyla birlikte nasıl Office.

## <a name="basic-multithreading-scenario"></a>Temel çoklu iş parçacığı okuma senaryosu
 Çözümlerde Office her zaman ana kullanıcı arabirimi iş parçacığında çalışır. Arka plan iş parçacığında ayrı bir görev çalıştırarak uygulama performansını düzleştirmeyi istiyor olabilir. Amaç, bir görev ve ardından diğer görev yerine aynı anda görünen iki görevi tamamlamaktır. Bu, yürütmenin daha sorunsuz tamamlanmasına (birden çok iş parçacığı kullanmanın ana nedeni) neden olur. Örneğin, ana Excel kullanıcı arabirimi iş parçacığında olay kodunuz olabilir ve arka plan iş parçacığında bir sunucudan veri topan ve Excel kullanıcı arabiriminde hücreleri sunucudan gelen verilerle güncelleştirme görevi çalıştırabilirsiniz.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Office nesne modeline çağrı Office iş parçacıkları
 Arka plan iş parçacığı uygulamanın Office, çağrı otomatik olarak STA sınırında sıralandı. Ancak, arka plan iş parçacığı Office uygulamanın çağrıyı işlemesi garanti edilemez. Çeşitli olasılıklar vardır:

1. Office uygulamanın, girme fırsatına sahip olması için çağrıya ileti göndermesi gerekir. Verim vermeden ağır işleme işlemi yapıyorsa bu işlem zaman alalır.

2. Başka bir mantıksal iş parçacığı zaten daire içinde ise, yeni iş parçacığı girebilirsiniz. Bu durum genellikle mantıksal bir iş parçacığı Office uygulamaya girin ve ardından çağıranın yalıtıcıya yeniden giriş çağrısı yaptığında gerçekleşir. Uygulamanın bu çağrının geri dönmesini beklemesi engellenmiş.

3. Excel, gelen çağrıyı hemen işleyene kadar bir durumda olabilir. Örneğin, Office uygulama kalıcı bir iletişim kutusu görüntüleniyor olabilir.

   2. ve 3. olasılıklar için [COM, IMessageFilter arabirimini](/windows/desktop/api/objidl/nn-objidl-imessagefilter) sağlar. Sunucu bunu uygulayıyorsa, tüm çağrılar [HandleIncomingCall yöntemi aracılığıyla](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) girin. 2. olasılık için çağrılar otomatik olarak reddedilir. 3. olasılık için sunucu, duruma bağlı olarak çağrıyı reddeder. Çağrı reddedilirse, ne yapacaklarını çağıranın karar vermesi gerekir. Normalde çağıranın [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter)uygulaması gerekir; bu durumda [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) yöntemi tarafından ret bildirilir.

   Ancak, Visual Studio'de Office geliştirme araçları kullanılarak oluşturulan çözümler söz Visual Studio, reddedilen tüm çağrıları ("İleti filtresi uygulamanın meşgul olduğunu gösteriyor") <xref:System.Runtime.InteropServices.COMException> dönüştürür. Bir arka plan iş parçacığında nesne modeli çağrısı her hazırlığında, bu özel durumu işlemeye hazır olun. Genellikle bu, belirli bir süre için yeniden denemeyi ve ardından bir iletişim kutusu görüntülemeyi içerir. Ancak, arka plan iş parçacığını STA olarak da oluşturabilir ve ardından bu iş parçacığı için bu durumu işlemek için bir ileti filtresi kaydedebilirsiniz.

## <a name="start-the-thread-correctly"></a>İş parçacığını doğru başlatma
 Yeni bir STA iş parçacığı oluşturmadan önce, iş parçacığını başlatmadan önce küme durumunu STA olarak ayarlayın. Aşağıdaki kod örneğinde bunun nasıl gerçekleştir olduğu gösterildi.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs" id="Snippet5":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb" id="Snippet5":::

 Daha fazla bilgi için [bkz. Yönetilen iş parçacığı en iyi yöntemleri.](/dotnet/standard/threading/managed-threading-best-practices)

## <a name="modeless-forms"></a>Modeless forms
 Modeless form, form görüntülenirken uygulamayla bir tür etkileşime izin verir. Kullanıcı formla etkileşime ve form da kapatmadan uygulamayla etkileşime geçmenizi sağlar. Nesne Office modeli yönetilen modeless formları destekler; ancak, bir arka plan iş parçacığında kullanılmamaları gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [İş Parçacığı (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [İş Parçacığı Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [İş parçacıklarını ve iş parçacığını kullanma](/dotnet/standard/threading/using-threads-and-threading)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
