---
title: Hedefleri ve Görevleri Yapılandırma | Microsoft Docs
description: Üzerinde MSBuild farklı bağlamları hedeflemek için MSBuild ile işlem dışında çalıştırmak üzere hedef ve görevleri yapılandırma.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 104f0926c60db823c7a77bacbc319823c975f35e7c1072284048b41c524e9758
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121270984"
---
# <a name="configure-targets-and-tasks"></a>Hedefleri ve görevleri yapılandırma

Üzerinde MSBuild farklı bağlamları hedeflemek için MSBuild ve görevleri MSBuild işlem dışında çalıştıracak şekilde yapılandırabilirsiniz. Örneğin, geliştirme bilgisayarı 64 bitlik bir .NET Framework 4.5 işletim sisteminde çalışırken 32 bit .NET Framework 2.0 uygulamasını hedefleyebilirsiniz. 4 veya daha önceki bir sürümle .NET Framework bilgisayarları da hedefleyebilirsiniz. 32 veya 64 bitliklik ve belirli .NET Framework birleşimi hedef bağlam *olarak bilinir.*

## <a name="installation"></a>Yükleme

  Yükleme paketini dosyadan MSBuild yüklemek Visual Studio, yükleme paketini indirmeden MSBuild [indirebilirsiniz.](https://www.microsoft.com/download/details.aspx?id=40760) Ayrıca kullanmak istediğiniz .NET Framework sürümlerini de yüklemeniz gerekir.

## <a name="targets-and-tasks"></a>Hedefler ve görevler

 MSBuild büyük bağlam kümelerini hedeflemek için belirli derleme görevlerini işlem dışında çalıştırır.  Örneğin, bir 32 bit MSBuild 64 bitlik bir bilgisayarı hedeflemek için 64 bit işlemde derleme görevi çalıştırabilirsiniz. Bu, bağımsız değişkenler `UsingTask` ve `Task` parametrelerle denetlenr. .NET Framework 4.5 tarafından yüklenmiş hedefler bu bağımsız değişkenleri ve parametreleri ayarlamış ve çeşitli hedef bağlamları için uygulama derlemek için hiçbir değişiklik gerekmez.

 Kendi hedef bağlamınızı oluşturmak için bu bağımsız değişkenleri ve parametreleri uygun şekilde ayarlamanız gerekir. Örnekler için .NET Framework 4.5 *Microsoft.Common.targets* dosyasına ve *Microsoft.Common.Tasks* dosyasına bakın.  Birden çok hedef bağlamla çalışan özel bir görev oluşturma veya mevcut görevleri değiştirme hakkında bilgi için bkz. Nasıl yapılandırılır: Hedefleri [ve görevleri yapılandırma.](../msbuild/how-to-configure-targets-and-tasks.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
