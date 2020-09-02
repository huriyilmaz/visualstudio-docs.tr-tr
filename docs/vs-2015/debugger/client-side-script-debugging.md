---
title: İstemci tarafı betik hata ayıklaması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], client-side scripts
- client-side scripts, debugging
ms.assetid: bb668527-2288-47bd-a6c8-cecbad76dde2
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6405a35068b7be7ac93eb91f4d9100e6a840b0bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702373"
---
# <a name="client-side-script-debugging"></a>İstemci Tarafı Betikte Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio hata ayıklayıcı, ASP.NET sayfalarındaki istemci tarafı betiklerdeki hataları bulmak ve düzeltmek için kapsamlı bir hata ayıklama ortamı sağlar.  
  
## <a name="opening-script-documents"></a>Betik belgelerini açma  
 Görüntülenecek **Çözüm Gezgini** sunucu tarafı ve istemci tarafı komut dosyası belgelerinin listesini görebilirsiniz. **Çözüm Gezgini**herhangi bir betik belgesini açabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: betik belgelerini görüntüleme](../debugger/how-to-view-script-documents.md).  
  
## <a name="breakpoint-mapping"></a>Kesme noktası eşleme  
 Visual Studio 'da, sunucu tarafı kodunda doğrudan hata ayıklayamazsınız, ancak sunucu tarafı dosyasında bir kesme noktası ayarlayabilirsiniz. Visual Studio, kesme noktasını istemci tarafı dosyasında karşılık gelen bir konumla otomatik olarak eşler ve istemci tarafı kodunda eşlenmiş bir kesme noktası oluşturur.  
  
## <a name="manually-or-automatically-attaching-to-script"></a>El ile veya otomatik olarak betiğe Iliştirme  
 ' De hata ayıklamayı başlatmak için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , hata ayıklayıcının hata ayıklamak istediğiniz betiğe eklemesi gerekir. Bu, el ile veya otomatik olarak gerçekleşebilir.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Eklemek istediğiniz çalışan bir betik işlemini seçmek için hata ayıklayıcı arabirimini kullanarak el ile iliştirebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: betiğe iliştirme](../debugger/how-to-attach-to-script.md).  
  
 Aşağıdaki işlemlerden biri gerçekleştiğinde hata ayıklayıcı otomatik olarak betiğe iliştirir:  
  
- Komut dosyasında ayarlanmış bir kesme noktasına ulaşırsınız.  
  
- Betik kodunuzda bir VBScript `Stop` ifadesine veya JScript `debugger` bildirimine gidersiniz.  
  
- Tarayıcı veya sunucu, betikte bir sözdizimi veya çalışma zamanı hatasıyla karşılaşır. Bu gerçekleştiğinde, bir iletişim kutusu görünür ve hata ayıklamaya Başla seçeneğini vardır.  
  
  Betiğe el ile iliştirtiğinizde, komut dosyası işlemi bir şekilde durduruluncaya kadar çalışmaya devam eder. **Hata Ayıkla** menüsünde **Kes** ' i seçerek bunu kesebilirsiniz.  
  
  Hata ayıklayıcı otomatik olarak eklendiğinde, kesme noktası, `Stop` Ekstre veya `debugger` deyimin ya da Hatanın gerçekleştiği veya Internet Explorer 'da hata ayıklamayı başlatmayı seçtiğiniz bir noktada betik yürütme durdurulur.  
  
  Bu noktada, hata ayıklamaya başlamak için normal hata ayıklayıcı tesislerini kullanabilirsiniz. Örneğin, kod satırlarınızı satıra göre yürütmeye devam etmek için **adım** komutlarını kullanabilirsiniz. Betik akışını görüntülemek ve denetlemek için **çağrı yığını** penceresini kullanabilirsiniz. Değişkenleri ve özellikleri görüntülemek veya değiştirmek için Windows veya **hemen** değişken penceresi kullanabilirsiniz.  
  
## <a name="enhanced-error-messages-for-script-debugging"></a>Betik hata ayıklaması için geliştirilmiş hata Iletileri  
 Visual Studio, yaygın betik hata ayıklama sorunları için gelişmiş hata iletileri sağlar. Internet Explorer 'a el ile iliştirmediğiniz sürece bu iletiler görüntülenmez. Internet Explorer otomatik olarak açıldığında bir hata durumuyla karşılaşırsanız, hata iletilerini görebilmeniz için el ile ekleme yapmayı deneyin.  
  
## <a name="debugging-ajax-script-applications"></a>AJAX betik uygulamalarında hata ayıklama  
 AJAX özellikli Web uygulamaları, komut dosyası kodunun yoğun bir şekilde kullanılmasını sağlar ve özel hata ayıklama zorluklarını yapar. AJAX hata ayıklama teknikleri hakkında daha fazla bilgi için bkz.  
  
 [Ajax uygulamalarına genel bakış ve hata ayıklama ve izleme](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Betik hata ayıklaması sınırlamaları](../debugger/limitations-on-script-debugging.md)   
 [Değişken pencereleri](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)   
 [Komut penceresi](../ide/reference/immediate-window.md)   
 [Ajax uygulamalarında hata ayıklama ve Izleme genel bakış](https://msdn.microsoft.com/library/92684ea0-7bb4-4a34-9203-3aa6394ce375)
