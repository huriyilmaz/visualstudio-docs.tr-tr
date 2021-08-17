---
title: Hedefleri ve görevleri yapılandırma | Microsoft Docs
description: MSBuild hedeflerini ve görevleri, üzerinde çalışmakta olduğunuz sunucudan farklı olan bağlamların hedeflemesini sağlamak için MSBuild ile işlem dışı çalışacak şekilde yapılandırın.
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
ms.openlocfilehash: e51a42e0dbe8eff311f22d704b15b2d558cc23b1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122055009"
---
# <a name="configure-targets-and-tasks"></a>Hedefleri ve görevleri yapılandırma

MSBuild hedeflerini ve görevleri, üzerinde çalışmakta olduğunuz sunucudan farklı olan bağlamların hedeflemesini sağlamak için MSBuild ile işlem dışı çalışacak şekilde yapılandırabilirsiniz. örneğin, geliştirme bilgisayarı 64-bit .NET Framework 4,5 işletim sisteminde çalışırken 32-bit .NET Framework 2,0 uygulamasını hedefleyebilirsiniz. .NET Framework 4 veya daha önceki bir sürümüyle çalışan bilgisayarları da hedefleyebilirsiniz. 32 veya 64-bit kullanımı ve belirli .NET Framework sürümünün birleşimi *hedef bağlam* olarak bilinir.

## <a name="installation"></a>Yükleme

  MSBuild Visual Studio 'den ayrı olarak yüklemek istiyorsanız yükleme paketini [MSBuild indirden](https://www.microsoft.com/download/details.aspx?id=40760)indirebilirsiniz. ayrıca, kullanmak istediğiniz .NET Framework sürümlerini de yüklemelisiniz.

## <a name="targets-and-tasks"></a>Hedefler ve görevler

 MSBuild, daha büyük bir bağlam kümesini hedeflemek için bazı yapı görevlerini işlem dışı çalıştırır.  örneğin, 32 bitlik bir MSBuild, 64-bit bir bilgisayarı hedeflemek için 64 bit işlemde bir yapı görevi çalıştırabilir. Bu, `UsingTask` bağımsız değişkenler ve parametreler tarafından denetlenir `Task` . .NET Framework 4,5 tarafından yüklenen hedefler, bu bağımsız değişkenleri ve parametreleri ayarlar ve çeşitli hedef bağlamlara yönelik uygulamalar oluşturmak için değişiklik gerektirmez.

 Kendi hedef bağlamınızı oluşturmak istiyorsanız, bu bağımsız değişkenleri ve parametreleri uygun şekilde ayarlamanız gerekir. örnekler için .NET Framework 4,5 *Microsoft. common. targets* dosyasına ve *Microsoft. Common. Tasks* dosyasına bakın.  Birden çok hedef bağlamda çalışan özel bir görevin nasıl oluşturulacağı veya mevcut görevlerin nasıl değiştirileceği hakkında bilgi için bkz. [nasıl yapılır: Configure targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
