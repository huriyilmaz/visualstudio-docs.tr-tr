---
title: Görevleri yapılandırma | Microsoft Docs
description: MSBuild görevlerini, üzerinde çalışmakta olduğunuz sunucudan farklı olan bağlamların hedeflemesini sağlamak için MSBuild ile işlem dışı çalışacak şekilde yapılandırın.
ms.custom: SEO-VS-2020
ms.date: 10/19/2021
ms.topic: conceptual
ms.assetid: 9aabe67a-1720-4bbf-80d3-822b3ccf75c0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 6c29e1a6a2b2e4544c94fe4837076a3d2dbbe3c3
ms.sourcegitcommit: efe1d737fd660cc9183177914c18b0fd4e39ba8b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2021
ms.locfileid: "130212809"
---
# <a name="configure-tasks"></a>Görevleri yapılandırma

görevleri, genel derlemeyi çalıştırana bilgisayardan farklı bağlamlarda çalıştırabilmeniz için, MSBuild ile işlem dışı çalışacak MSBuild hedeflerini ve görevleri yapılandırabilirsiniz. bu, 64 bit MSBuild uyumlu olmayan görevleri çalıştırırken ve .NET Framework farklı bir sürümü hedeflerken yararlı olabilir. 

örneğin, geliştirme bilgisayarı 64-bit .NET Framework 4,5 işletim sisteminde çalışırken 32-bit .NET Framework 2,0 uygulamasını hedefleyebilirsiniz. .NET Framework 4 veya daha önceki bir sürümüyle çalışan bilgisayarları da hedefleyebilirsiniz. 32 veya 64-bit kullanımı ve belirli .NET Framework sürümünün birleşimi *hedef bağlam* olarak bilinir.

## <a name="tasks"></a>Görevler

 MSBuild, daha büyük bir bağlam kümesini hedeflemek için bazı yapı görevlerini işlem dışı çalıştırır.  örneğin, 32 bit MSBuild bir yapı görevini 64 bit bir işlemde çalıştırabilir. Bu, `UsingTask` bağımsız değişkenler ve parametreler tarafından denetlenir `Task` . .NET Framework 4,5 tarafından yüklenen hedefler, bu bağımsız değişkenleri ve parametreleri ayarlar ve çeşitli hedef bağlamlara yönelik uygulamalar oluşturmak için değişiklik gerektirmez.

 Kendi hedef bağlamınızı oluşturmak istiyorsanız, bu bağımsız değişkenleri ve parametreleri uygun şekilde ayarlamanız gerekir. örnekler için .NET Framework 4,5 *Microsoft. common. targets* dosyasına ve *Microsoft. Common. Tasks* dosyasına bakın.  Birden çok hedef bağlamda çalışan özel bir görevin nasıl oluşturulacağı veya mevcut görevlerin nasıl değiştirileceği hakkında bilgi için bkz. [nasıl yapılır: Configure targets and Tasks](../msbuild/how-to-configure-targets-and-tasks.md).

## <a name="errors-arising-from-incorrect-configuration"></a>Yanlış yapılandırmadan kaynaklanan hatalar

Yapılandırmadaki hatalar, [MSB4018](../msbuild/errors/msb4018.md) veya [MSB4062](../msbuild/errors/msb4062.md) hatalarıyla başarısız olan görevlerle sonuçlanabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
