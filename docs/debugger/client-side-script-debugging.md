---
title: İstemci tarafı betik hata ayıklaması | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f9f66d757f5f46530619be1424eb0810ce546ff5
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745707"
---
# <a name="client-side-script-debugging"></a>İstemci Tarafı Betikte Hata Ayıklama
Visual Studio hata ayıklayıcı, ASP.NET sayfalarındaki istemci tarafı betiklerdeki hataları bulmak ve düzeltmek için kapsamlı bir hata ayıklama ortamı sağlar.

## <a name="opening-script-documents"></a>Betik belgelerini açma
Görüntülenecek **Çözüm Gezgini** sunucu tarafı ve istemci tarafı komut dosyası belgelerinin listesini görebilirsiniz. **Çözüm Gezgini**herhangi bir betik belgesini açabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: betik belgelerini görüntüleme](../debugger/how-to-view-script-documents.md).

## <a name="breakpoint-mapping"></a>Kesme noktası eşleme
 Visual Studio 'da, sunucu tarafı kodunda doğrudan hata ayıklayamazsınız, ancak sunucu tarafı dosyasında bir kesme noktası ayarlayabilirsiniz. Visual Studio, kesme noktasını istemci tarafı dosyasında karşılık gelen bir konumla otomatik olarak eşler ve istemci tarafı kodunda eşlenmiş bir kesme noktası oluşturur.

## <a name="manually-or-automatically-attaching-to-script"></a>El ile veya otomatik olarak betiğe Iliştirme
 @No__t_0 betiği hata ayıklamaya başlamak için, hata ayıklayıcının hata ayıklamak istediğiniz betiğe eklemesi gerekir. Bu, el ile veya otomatik olarak gerçekleşebilir.

 Eklemek istediğiniz çalışan bir betik işlemini seçmek için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hata ayıklayıcı arabirimini kullanarak el ile iliştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: betiğe iliştirme](../debugger/how-to-attach-to-script.md).

 Aşağıdaki işlemlerden biri gerçekleştiğinde hata ayıklayıcı otomatik olarak betiğe iliştirir:

- Komut dosyasında ayarlanmış bir kesme noktasına ulaşırsınız.

- Betik kodunuzda bir VBScript `Stop` ifadesine veya JScript `debugger` ifadesine ulaşırsınız.

- Tarayıcı veya sunucu, betikte bir sözdizimi veya çalışma zamanı hatasıyla karşılaşır. Bu gerçekleştiğinde, bir iletişim kutusu görünür ve hata ayıklamaya Başla seçeneğini vardır.

  Betiğe el ile iliştirtiğinizde, komut dosyası işlemi bir şekilde durduruluncaya kadar çalışmaya devam eder. **Hata Ayıkla** menüsünde **Kes** ' i seçerek bunu kesebilirsiniz.

  Hata ayıklayıcı otomatik olarak eklendiğinde, komut dosyası yürütme, kesme noktası, `Stop` deyimin veya `debugger` deyimin ya da Hatanın gerçekleştiği veya Internet Explorer 'da hata ayıklamayı başlatmayı seçtiğiniz noktada durdurulur.

  Bu noktada, hata ayıklamaya başlamak için normal hata ayıklayıcı tesislerini kullanabilirsiniz. Örneğin, kod satırlarınızı satıra göre yürütmeye devam etmek için **adım** komutlarını kullanabilirsiniz. Betik akışını görüntülemek ve denetlemek için **çağrı yığını** penceresini kullanabilirsiniz. Değişkenleri ve özellikleri görüntülemek veya değiştirmek için Windows veya **hemen** değişken penceresi kullanabilirsiniz.

## <a name="enhanced-error-messages-for-script-debugging"></a>Betik hata ayıklaması için geliştirilmiş hata Iletileri
 Visual Studio, yaygın betik hata ayıklama sorunları için gelişmiş hata iletileri sağlar. Internet Explorer 'a el ile iliştirmediğiniz sürece bu iletiler görüntülenmez. Internet Explorer otomatik olarak açıldığında bir hata durumuyla karşılaşırsanız, hata iletilerini görebilmeniz için el ile ekleme yapmayı deneyin.

## <a name="debugging-ajax-script-applications"></a>AJAX betik uygulamalarında hata ayıklama
 AJAX özellikli Web uygulamaları, komut dosyası kodunun yoğun bir şekilde kullanılmasını sağlar ve özel hata ayıklama zorluklarını yapar. AJAX hata ayıklama teknikleri hakkında daha fazla bilgi için bkz.

 [Ajax uygulamalarına genel bakış ve hata ayıklama ve izleme](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375).

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET ve AJAX Uygulamalarında Hata Ayıklama](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)
- [Betik Hata Ayıklama Sınırlamaları](../debugger/limitations-on-script-debugging.md)
- [Değişken pencereleri](../debugger/debugger-windows.md)
- [Komut Penceresi](../ide/reference/immediate-window.md)
- [Ajax uygulamalarında hata ayıklama ve Izleme genel bakış](https://msdn.microsoft.com/Library/92684ea0-7bb4-4a34-9203-3aa6394ce375)