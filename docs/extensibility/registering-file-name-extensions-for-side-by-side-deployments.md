---
title: Yan Yana Dağıtımlar için Dosya Adı Uzantılarını Kaydetme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6717625a44b48a25d293f68d01cd9fa3c7c24853
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701547"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Yan yana dağıtımlar için dosya adı uzantılarını kaydetme
Yan yana dağıtılan VSPackages için, dosyaları doğru sürümüyle ilişkilendirmek için dosya adı uzantılarını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]kaydetmeniz gerekir. Sürüme özel bir dosya adı uzantısı kullanmadığınız sürece, kayıt kullanıcıların projenizi ve [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]proje öğesi dosyalarınızı uygun sürümünde açmalarını sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [Dosya adı uzantıları hakkında](../extensibility/about-file-name-extensions.md) Dosya adı uzantılarının nasıl kaydolduğunu tartışır.

- [Dosya adı uzantıları için dosya işleyicileri belirtin](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Belirli bir dosya adı uzantısını açabilecek, bunları ve benzeri uygulamaları nasıl kaydedebileceğihakkında bilgi sağlar.

- [Dosya adı uzantıları için fiilleri kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md) Fiillerin nasıl kaydedilenini tartışır.

- [Yan yana dosya ilişkilendirmelerini yönetme](../extensibility/managing-side-by-side-file-associations.md) Bir dosyayı açmak için belirli bir sürümün [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] çağrılması gereken yan yana yüklemelerin nasıl işleyeceğini tartışır.

## <a name="related-sections"></a>İlgili bölümler
- [Visual Studio'nun birden fazla versiyonunu destekleyin](../extensibility/supporting-multiple-versions-of-visual-studio.md) Geliştirme [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve son kullanıcılara dağıtım sırasında VSPackage'ınızın birden çok sürümü ve VSPackage ile ilgili sorunları açıklar.
