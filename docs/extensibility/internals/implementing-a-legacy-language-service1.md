---
title: Eski Dil Hizmetinin Uygulanması1 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707694"
---
# <a name="implementing-a-legacy-language-service"></a>Eski Dil Hizmeti Uygulama
Yönetilen paket çerçevesindeki (MPF) sınıfları, sözdizimi vurgulama, ayraç eşleştirme ve IntelliSense tamamlama gibi çok çeşitli özellikleri destekleyen eski bir dil hizmeti uygulamak için kullanabilirsiniz.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Bir dil hizmetini uygulamanın yeni yolu hakkında daha fazla bilgi edinmek için [Editör ve Dil Hizmeti Uzantıları'na](../../extensibility/editor-and-language-service-extensions.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="in-this-section"></a>Bu Bölümde
- [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)

 MPF'de desteklenen dil hizmeti özelliklerine genel bakış.

- [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 MPF kullanarak bir dil hizmeti uygulamak için gerekenleri açıklar.

- [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)

 MPF tabanlı bir dil hizmetini [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

- [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 MPF kullanarak bir dil hizmetinin tüm özelliklerini uygulamak için gereken iki ayrıştırıcıyı açıklar.

- [İzlenecek Yol: Eski Dil Hizmeti Oluşturma](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 VSPackage'da MPF dil hizmeti uygulamak için gereken temel adımları sağlar.

- [İzlenecek Yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Yüklü kod parçacıklarının listesini alma tekniklerini gösterir.

- [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)

 MPF kullanarak bir dil hizmetinin tüm özelliklerini uygulamak için ne yapılması gerektiğini ayrıntılı olarak açıklayan konulara bağlantılar sağlar.
