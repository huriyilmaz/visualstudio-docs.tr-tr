---
title: Office 'te iş parçacığı desteği
description: İş parçacığı Microsoft Office nesne modelinde desteklenir. Office nesne modeli iş parçacığı açısından güvenli değildir, ancak bir Office çözümünde birden çok iş parçacığı ile çalışabilir.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5d44c86e17b5df79c44f85cd555b3036e925ae61
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524187"
---
# <a name="threading-support-in-office"></a>Office 'te iş parçacığı desteği
  Bu makalede, iş parçacığı Microsoft Office nesne modelinde nasıl desteklenmiş hakkında bilgi sağlanır. Office nesne modeli iş parçacığı açısından güvenli değildir, ancak bir Office çözümünde birden çok iş parçacığı ile çalışmak mümkündür. Office uygulamaları bileşen nesne modeli (COM) sunucularıdır. COM, istemcilerin rastgele iş parçacıklarında COM sunucuları çağırmasını sağlar. COM, iş parçacığı güvenli olmayan COM sunucuları için, aynı anda yalnızca bir mantıksal iş parçacığının sunucuda yürütüldüğü şekilde eşzamanlı çağrıları seri hale getirmek için bir mekanizma sağlar. Bu mekanizma tek iş parçacıklı Apartment (STA) modeli olarak bilinir. Çağrılar serileştirildiği için, sunucu meşgul olduğu veya bir arka plan iş parçacığında diğer çağrıları işlediği için çağıranlar zaman dilimleri engellenebilir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="knowledge-required-when-using-multiple-threads"></a>Birden çok iş parçacığı kullanılırken gereken bilgi
 Birden çok iş parçacığı ile çalışmak için, çoklu iş parçacığı oluşturma yönlerinin en az temel bilgisine sahip olmanız gerekir:

- Windows API 'Leri

- COM çok iş parçacıklı kavramlar

- Eşzamanlılık

- Eşitleme

- Hazırlama

  Çoklu iş parçacığı oluşturma hakkında genel bilgi için bkz. [yönetilen iş parçacığı](/dotnet/standard/threading/).

  Office ana STA 'da çalışır. Bunun etkilerini anlamak, Office ile birden çok iş parçacığının nasıl kullanılacağını anlamanıza olanak tanır.

## <a name="basic-multithreading-scenario"></a>Temel çoklu iş parçacığı senaryosu
 Office çözümlerinde kod, her zaman ana kullanıcı arabirimi iş parçacığında çalışır. Arka plan iş parçacığında ayrı bir görev çalıştırarak uygulama performansını düzgünleştirmek isteyebilirsiniz. Amaç, tek bir görev yerine diğer iki görevi tamamen tamamlamadır. Bu, daha yumuşak yürütmeye neden olması gerekir (birden çok iş parçacığı kullanmanın asıl nedeni). Örneğin, ana Excel UI iş parçacığında olay kodunuz olabilir ve bir arka plan iş parçacığında, bir sunucudan veri toplayan ve Excel Kullanıcı arabirimindeki hücreleri sunucudaki verilerle güncelleştiren bir görevi çalıştırabilirsiniz.

## <a name="background-threads-that-call-into-the-office-object-model"></a>Office nesne modeline çağıran arka plan iş parçacıkları
 Bir arka plan iş parçacığı Office uygulamasına bir çağrı yaptığında, çağrı otomatik olarak STA sınırları üzerinden sıralanır. Ancak, arka plan iş parçacığı yaptığı sırada Office uygulamasının çağrıyı işleyebileceğini garanti etmez. Birçok olasılık vardır:

1. Office uygulamasının, çağrı için, girme fırsatına sahip olan iletileri göndericisi gerekir. Bu işlem gerçekleşmeksizin ağır işleme alıyorsa zaman alabilir.

2. Zaten grupta başka bir mantıksal iş parçacığı varsa, yeni iş parçacığı giremezsiniz. Bu durum genellikle, bir mantıksal iş parçacığı Office uygulamasına girdiğinde ve sonra çağıranın Apartmanı geri çağırma yaptığında gerçekleşir. Uygulama, bu çağrının dönmesi için beklerken engellendi.

3. Excel, gelen çağrıyı hemen işleyememesi gibi bir durumda olabilir. Örneğin, Office uygulaması kalıcı bir iletişim kutusu görüntülüyor olabilir.

   2 ve 3 olasılıkları için, COM [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) arabirimini sağlar. Sunucu uygularsa, tüm çağrılar [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) yöntemi aracılığıyla girer. 2. olasılık için çağrılar otomatik olarak reddedilir. 3. olasılık için sunucu, koşullara bağlı olarak çağrıyı reddedebilir. Çağrı reddedilirse, çağıranın ne yapacağına karar vermelidir. Normalde, çağıran [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter)'ı uygular, bu durumda [RetryRejectedCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) yöntemi tarafından ret için bildirim yapılır.

   Ancak, Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan çözümler söz konusu olduğunda COM birlikte çalışması, reddedilen tüm çağrıları bir <xref:System.Runtime.InteropServices.COMException> ("uygulamanın meşgul olduğunu belirten ileti filtresi") olarak dönüştürür. Bir arka plan iş parçacığında bir nesne modeli çağrısı yaptığınızda, bu özel durumu işlemeye hazır olmanız gerekir. Genellikle, belirli bir süre için yeniden denemeyi ve sonra bir iletişim kutusunu görüntülemeyi içerir. Ancak, arka plan iş parçacığını STA olarak da oluşturabilir ve ardından bu durumu işlemek için bu iş parçacığına bir ileti filtresi kaydedebilirsiniz.

## <a name="start-the-thread-correctly"></a>İş parçacığını doğru şekilde başlatın
 Yeni bir STA iş parçacığı oluşturduğunuzda, iş parçacığına başlamadan önce grup durumunu STA olarak ayarlayın. Aşağıdaki kod örneği bunun nasıl yapılacağını göstermektedir.

 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]

 Daha fazla bilgi için bkz. [yönetilen iş parçacığı en iyi yöntemleri](/dotnet/standard/threading/managed-threading-best-practices).

## <a name="modeless-forms"></a>Modsuz formlar
 Kalıcı olmayan bir form, form görüntülenirken uygulamayla ilgili bazı etkileşim türlerine izin verir. Kullanıcı formla etkileşime girer ve form, kapatma olmadan uygulamayla etkileşime girer. Office nesne modeli, yönetilen modsuz formları destekler; Ancak, bir arka plan iş parçacığında kullanılmamalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [İş parçacığı oluşturma (C#)](/dotnet/csharp/programming-guide/concepts/threading/index)
- [İş parçacığı (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/threading/index)
- [İş parçacıkları ve iş parçacığı kullanma](/dotnet/standard/threading/using-threads-and-threading)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
