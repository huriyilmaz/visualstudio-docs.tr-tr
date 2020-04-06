---
title: Eski Dil Hizmeti Genişletilebilirlik | Microsoft Dokümanlar
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
ms.openlocfilehash: 81b5ec3de8d7b0b9466e162c3ee193c130634cd4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707404"
---
# <a name="legacy-language-service-extensibility"></a>Eski Dil Hizmeti Genişletilebilirliği
Dil hizmeti, IDE'de kaynak kodu düzenlemek için dile özel destek sağlar.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Bir dil hizmetini uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Editör ve Dil Hizmeti Uzantıları'na](../../extensibility/editor-and-language-service-extensions.md)bakın.

 Bu bölümde, eski bir dil hizmetinin yapısı ve uygulanması tartışılmaktadır.

## <a name="in-this-section"></a>Bu Bölümde
- [Eski Dil Hizmetini Geçirme](../../extensibility/internals/migrating-a-legacy-language-service.md)

 Visual Studio 2008'den en son sürüme bir dil hizmetinin nasıl güncelleştirilebildiğini açıklar.

- [Eski Dil Hizmeti Temel Bileşenleri](../../extensibility/internals/legacy-language-service-essentials.md)

 Visual Studio'ya bir programlama dilini entegre etmek için dil hizmetlerinin nasıl geliştirileceklerine ilişkin önemli bilgiler sağlar.

- [Eski Dil Hizmeti Geliştirme](../../extensibility/internals/developing-a-legacy-language-service.md)

 Bir dil hizmeti oluşturmanıza yardımcı olabilecek konulara bağlantılar sağlar.

- [Eski Dil Hizmetinde Söz Dizimi Renklendirmesi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Bir dil hizmetinde sözdizimi vurgulamayı destekleme hakkında bilgi sağlar.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service1.md)

 Yönetilen kodda tam özellikli bir dil hizmeti uygulamak için yönetilen paket çerçevesinin (MPF) nasıl kullanılacağı hakkında bilgi sağlar.

- [Sembol Tarama Araçlarını Destekleme](../../extensibility/internals/supporting-symbol-browsing-tools.md)

 IDE'deki sembollerin ağaç görünümlerine göz atmanızı sağlayan kitaplıkları ve araçları açıklar.

## <a name="related-sections"></a>İlgili Bölümler
- [Düzenleyici ve Dil Hizmeti Uzantıları](../../extensibility/editor-and-language-service-extensions.md)

 Visual Studio editörlerine genel bir bakış sağlar.

- [Hata Ayıklama için Dil Hizmeti Desteği](../../extensibility/internals/language-service-support-for-debugging.md)

 Veri ayıklama programları için kullanılan hata ayıklama bileşenlerioluşturmak ve özelleştirmek için gereken bilgileri içeren Visual Studio Hata Ayıklama SDK hakkında bilgi ve bağlantı sağlar.
