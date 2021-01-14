---
title: Eski dil hizmeti genişletilebilirliği | Microsoft Docs
description: Visual Studio 'da eski dil hizmetlerinin yapısı, uygulanması ve genişletilebilirliği hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 313d1d7bb74ccb456173474f7f0e3140814755bd
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205079"
---
# <a name="legacy-language-service-extensibility"></a>Eski Dil Hizmeti Genişletilebilirliği
Dil hizmeti, IDE 'de kaynak kodu düzenlemede dile özgü destek sağlar.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Dil hizmeti uygulama hakkında daha fazla bilgi edinmek için bkz. [Düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).

 Bu bölümde, eski dil hizmetinin yapısı ve uygulanması açıklanmaktadır.

## <a name="in-this-section"></a>Bu Bölümde
- [Eski Dil Hizmetini Geçirme](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Visual Studio 2008 ' den en son sürüme bir dil hizmetinin nasıl güncelleştireceğinizi açıklar.

- [Eski Dil Hizmeti Temel Bileşenleri](../../extensibility/internals/legacy-language-service-essentials.md)

 Programlama dilini Visual Studio 'ya bütünleştirmek için dil hizmetleri geliştirme hakkında önemli bilgiler sağlar.

- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)

 Dil hizmeti oluşturmanıza yardımcı olabilecek konuların bağlantılarını sağlar.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Dil hizmetinde sözdizimi vurgulamayı destekleme hakkında bilgi sağlar.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Yönetilen kodda tam özellikli bir dil hizmeti uygulamak için yönetilen paket çerçevesi 'nin (MPF) nasıl kullanılacağı hakkında bilgi sağlar.

- [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 IDE 'deki sembolleri ağaç görünümlerine gözatmanızı sağlayan kitaplıkları ve araçları açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Düzenleyici ve Dil Hizmeti Uzantıları](../../extensibility/editor-and-language-service-extensions.md)

 Visual Studio düzenleyicilerine genel bakış sağlar.

- [Hata Ayıklama için Dil Hizmeti Desteği](../../extensibility/internals/language-service-support-for-debugging.md)

 Ve programlarında hata ayıklama için kullanılan hata ayıklayıcı bileşenlerini oluşturmak ve özelleştirmek için gereken bilgileri içeren Visual Studio hata ayıklama SDK 'Sı ile ilgili bilgiler sağlar.
