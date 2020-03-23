---
title: Hedeflerin ve Görevlerin Yapılandırılması | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 39a3d6ba3eff6a01c2d0ff68b4132d883eadb90f
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634402"
---
# <a name="configure-targets-and-tasks"></a>Hedefleri ve görevleri yapılandırma

MSBuild hedeflerini ve görevlerini, üzerinde çalışan içeriklerden farklı bağlamları hedefleyebilmeniz için MSBuild ile işlem dışı çalışacak şekilde yapılandırabilirsiniz. Örneğin, geliştirme bilgisayarı 64 bit .NET Framework 4.5 işletim sistemi üzerinde çalışırken 32 bit .NET Framework 2.0 uygulamasını hedefleyebilirsiniz. .NET Framework 4 veya daha önce siyle çalışan bilgisayarları da hedefleyebilirsiniz. 32 veya 64 bitlik ve belirli .NET Framework sürümünün birleşimi *hedef bağlam*olarak bilinir.

## <a name="installation"></a>Yükleme

  MSBuild'i Visual Studio'dan ayrı olarak yüklemek istiyorsanız, yükleme paketini [MSBuild'ten indirebilirsiniz.](https://www.microsoft.com/download/details.aspx?id=40760) Kullanmak istediğiniz .NET Framework sürümlerini de yüklemeniz gerekir.

## <a name="targets-and-tasks"></a>Hedefler ve görevler

 MSBuild, daha büyük bir bağlam kümesini hedeflemek için belirli yapı görevlerini işlem dışı çalıştırıyor.  Örneğin, 32 bit MSBuild, 64 bitlik bir bilgisayarı hedeflemek için 64 bit işlemde bir yapı görevi çalıştırabilir. Bu bağımsız `UsingTask` değişkenler `Task` ve parametreler tarafından denetlenir. .NET Framework 4.5 tarafından yüklenen hedefler bu bağımsız değişkenleri ve parametreleri belirler ve çeşitli hedef bağlamlar için uygulama oluşturmak için herhangi bir değişiklik gerekmez.

 Kendi hedef bağlamınızı oluşturmak istiyorsanız, bu bağımsız değişkenleri ve parametreleri uygun şekilde ayarlamanız gerekir. .NET Framework 4.5 *Microsoft.Common.targets* dosyasına ve örnekler için *Microsoft.Common.Tasks* dosyasına bakın.  Birden çok hedef bağlamıyla çalışabilen özel bir görevin nasıl oluşturulabileceği veya varolan görevlerin nasıl değiştirilebildiği hakkında bilgi için [bkz.](../msbuild/how-to-configure-targets-and-tasks.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
