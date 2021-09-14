---
title: Yan yana IDE'ler için dosya adı uzantılarını kaydetme
description: Kullanıcıların dosyaları uygulamanın uygun sürümünde açmalarını sağlayan yan yana dağıtımlar için dosya adı uzantılarını kaydetmeyi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- file extensions, registering for side-by-side
ms.assetid: 9ab046a2-147d-4167-aa14-7d661b1eaaa5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: be7c5c2a45d42840c41b5860596cc4fd8c883bf0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626007"
---
# <a name="register-file-name-extensions-for-side-by-side-deployments"></a>Yan yana dağıtımlar için dosya adı uzantılarını kaydetme
Yan yana ortamda dağıtılan VSPackage'lar için, dosyaları doğru sürümüyle ilişkilendirmek için dosya adı uzantılarını kaydetmeniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] gerekir. Sürüme özgü bir dosya adı uzantısı kullanmadıkça kayıt, kullanıcıların projenizi ve proje öğesi dosyalarınızı uygun sürümünde açmalarını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sağlar.

## <a name="in-this-section"></a>Bu bölümde
- [Dosya adı uzantıları hakkında](../extensibility/about-file-name-extensions.md) Dosya adı uzantılarının nasıl kaydedildiklerini tartışır.

- [Dosya adı uzantıları için dosya işleyicileri belirtme](../extensibility/specifying-file-handlers-for-file-name-extensions.md) Belirli bir dosya adı uzantısını aç, düzenle ve diğer uygulamaları kaydetme hakkında bilgi sağlar.

- [Dosya adı uzantıları için fiilleri kaydetme](../extensibility/registering-verbs-for-file-name-extensions.md) Fiillerin nasıl kaydedil olduğunu tartışan.

- [Yan yana dosya ilişkilendirmelerini yönetme](../extensibility/managing-side-by-side-file-associations.md) Bir dosyayı açmak için belirli bir sürümünün çağrılsı gereken yan yana [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklemelerin nasıl iş gerektiğini ele almaktadır.

## <a name="related-sections"></a>İlgili bölümler
- [Birden çok sürüm desteği Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md) Son kullanıcılara geliştirme ve dağıtım sırasında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] birden çok sürümü ve VSPackage ile ilgili sorunları açıklar.
