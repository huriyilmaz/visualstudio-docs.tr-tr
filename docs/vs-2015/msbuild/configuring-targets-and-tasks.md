---
title: Hedefleri ve görevleri yapılandırma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 892e9615599a8881e219c00f748a0cc1567d996d
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850041"
---
# <a name="configuring-targets-and-tasks"></a>Hedefleri ve Görevleri Yapılandırma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Üzerinde çalışmakta olduğunuz sunucudan farklı olan bağlamların hedeflemesini sağlamak için MSBuild ile işlem dışı çalışacak MSBuild hedeflerini ve görevlerini yapılandırabilirsiniz. Örneğin, geliştirme bilgisayarı 64-bit .NET Framework 4,5 işletim sisteminde çalışırken 32-bit .NET Framework 2,0 uygulamasını hedefleyebilirsiniz. .NET Framework 4 veya daha önceki bir sürümüyle çalışan bilgisayarları da hedefleyebilirsiniz. 32 veya 64-bit kullanımı ve belirli .NET Framework sürümünün birleşimi *hedef bağlam*olarak bilinir.  
  
## <a name="installation"></a>Yükleme  
 .NET Framework 4,5 ve 4.5.1, ortak dil çalışma zamanını (CLR), hedefleri, görevleri ve .NET Framework 4 ' ün yeniden adlandırmadan araç olarak değiştirir. .NET Framework 4.5.1, Bölüm [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]olarak yüklenir.  
  
 MSBuild 'i Visual Studio 'dan ayrı olarak yüklemek istiyorsanız yükleme paketini [MSBuild indirinden](https://www.microsoft.com/download/details.aspx?id=40760)indirebilirsiniz. Ayrıca, kullanmak istediğiniz .NET Framework sürümlerini de yüklemelisiniz.  
  
## <a name="targets-and-tasks"></a>Hedefler ve Görevler  
 MSBuild, bazı yapı görevlerini, daha büyük bir bağlam kümesini hedeflemek için işlem dışında çalıştırır.  Örneğin, 32 bitlik bir MSBuild, 64-bit bir bilgisayarı hedeflemek için 64 bit işlemde bir Build görevi çalıştırabilir. Bu, `UsingTask` bağımsız değişkenlerle ve `Task` parametreleriyle denetlenir. .NET Framework 4,5 tarafından yüklenen hedefler, bu bağımsız değişkenleri ve parametreleri ayarlar ve çeşitli hedef bağlamlara yönelik uygulamalar oluşturmak için değişiklik gerektirmez.  
  
 Kendi hedef bağlamınızı oluşturmak istiyorsanız, bu bağımsız değişkenleri ve parametreleri uygun şekilde ayarlamanız gerekir. Örnekler için .NET Framework 4,5 Microsoft. Common. targets dosyasına ve Microsoft. Common. Tasks dosyasına bakın.  Birden çok hedef bağlamda çalışan özel bir görevin nasıl oluşturulacağı veya mevcut görevlerin nasıl değiştirileceği hakkında bilgi için bkz. [nasıl yapılır: Configure targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
