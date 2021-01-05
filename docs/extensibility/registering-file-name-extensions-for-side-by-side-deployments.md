---
title: Yan yana Ides için dosya adı uzantılarını Kaydet
description: Kullanıcıların Visual Studio 'nun uygun sürümünde dosya açmasına olanak tanıyan yan yana dağıtımlar için dosya adı uzantılarını kaydetme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c66413890f0aaa08e09a291f5bf31a44e7c24706
ms.sourcegitcommit: dd96a95d87a039525aac86abe689c30e2073ae87
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2021
ms.locfileid: "97863037"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Yan yana dağıtımlar için dosya adı uzantılarını kaydetme
Yan yana bir ortamda dağıtılan VSPackages 'ler için, dosyaları doğru sürümü ile ilişkilendirmek üzere dosya adı uzantılarını kaydetmeniz gerekir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Sürüme özgü bir dosya adı uzantısı kullanmıyorsanız, kayıt, kullanıcıların projenizi ve proje öğesi dosyalarını uygun sürümünde açmasına olanak sağlar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>Bu bölümde
- [Dosya adı uzantıları hakkında](../extensibility/about-file-name-extensions.md) Dosya adı uzantılarının nasıl kaydedildiğini açıklar.

- [Dosya adı uzantıları için dosya Işleyicileri belirtin](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Belirli bir dosya adı uzantısını açan, düzenleyebilen ve bu uygulamaların nasıl kaydedileceği hakkında bilgi sağlar.

- [Dosya adı uzantıları için fiilleri kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md) Fiillerin nasıl kaydedileceği açıklanmaktadır.

- [Yan yana dosya Ilişkilendirmelerini yönetme](../extensibility/managing-side-by-side-file-associations.md) Belirli bir sürümünün [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bir dosyayı açmak için çağrılması gereken yan yana yüklemelerin nasıl işleneceğini açıklar.

## <a name="related-sections"></a>İlgili bölümler
- [Visual Studio 'nun birden çok sürümünü destekleme](../extensibility/supporting-multiple-versions-of-visual-studio.md) Uygulamasının, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] son kullanıcılara geliştirme ve dağıtım sırasında birden fazla sürümü ve VSPackage ile ilgili sorunları açıklar.
