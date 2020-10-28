---
title: Hedefleri ve görevleri yapılandırma | Microsoft Docs
description: Üzerinde çalışmakta olduğunuz sunucudan farklı olan bağlamların hedeflemesini sağlamak için MSBuild ile işlem dışı çalışacak MSBuild hedeflerini ve görevleri yapılandırın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 46f1f96708af6f5d99affead4d47c1f35db5dc4a
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796244"
---
# <a name="configure-targets-and-tasks"></a>Hedefleri ve görevleri yapılandırma

Üzerinde çalışmakta olduğunuz sunucudan farklı olan bağlamların hedeflemesini sağlamak için MSBuild ile işlem dışı çalışacak MSBuild hedeflerini ve görevlerini yapılandırabilirsiniz. Örneğin, geliştirme bilgisayarı 64-bit .NET Framework 4,5 işletim sisteminde çalışırken 32-bit .NET Framework 2,0 uygulamasını hedefleyebilirsiniz. .NET Framework 4 veya daha önceki bir sürümüyle çalışan bilgisayarları da hedefleyebilirsiniz. 32 veya 64-bit kullanımı ve belirli .NET Framework sürümünün birleşimi *hedef bağlam* olarak bilinir.

## <a name="installation"></a>Yükleme

  MSBuild 'i Visual Studio 'dan ayrı olarak yüklemek istiyorsanız yükleme paketini [MSBuild indirinden](https://www.microsoft.com/download/details.aspx?id=40760)indirebilirsiniz. Ayrıca, kullanmak istediğiniz .NET Framework sürümlerini de yüklemelisiniz.

## <a name="targets-and-tasks"></a>Hedefler ve görevler

 MSBuild, bazı yapı görevlerini, daha büyük bir bağlam kümesini hedeflemek için işlem dışında çalıştırır.  Örneğin, 32 bitlik bir MSBuild, 64-bit bir bilgisayarı hedeflemek için 64 bit işlemde bir Build görevi çalıştırabilir. Bu, `UsingTask` bağımsız değişkenler ve parametreler tarafından denetlenir `Task` . .NET Framework 4,5 tarafından yüklenen hedefler, bu bağımsız değişkenleri ve parametreleri ayarlar ve çeşitli hedef bağlamlara yönelik uygulamalar oluşturmak için değişiklik gerektirmez.

 Kendi hedef bağlamınızı oluşturmak istiyorsanız, bu bağımsız değişkenleri ve parametreleri uygun şekilde ayarlamanız gerekir. Örnekler için .NET Framework 4,5 *Microsoft. Common. targets* dosyasına ve *Microsoft. Common. Tasks* dosyasına bakın.  Birden çok hedef bağlamda çalışan özel bir görevin nasıl oluşturulacağı veya mevcut görevlerin nasıl değiştirileceği hakkında bilgi için bkz. [nasıl yapılır: Configure targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu sürüm desteği](../msbuild/msbuild-multitargeting-overview.md)
