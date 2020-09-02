---
title: Eski dil Service1 uygulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20493991d8e0740ca045f041e2ba94cf3735ad1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64816399"
---
# <a name="implementing-a-legacy-language-service"></a>Eski Dil Hizmeti Uygulama
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sözdizimi vurgulama, küme ayracı eşleştirme ve IntelliSense tamamlama gibi çok çeşitli özellikleri destekleyen eski bir dil hizmetini uygulamak için yönetilen paket çerçevesi 'nde (MPF) sınıfları kullanabilirsiniz.  
  
 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Dil hizmeti uygulama hakkında daha fazla bilgi edinmek için bkz. [Düzenleyici ve dil hizmeti uzantıları](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski Dil Hizmetine Genel Bakış](../../extensibility/internals/legacy-language-service-overview.md)  
 MPF 'de desteklenen dil hizmeti özelliklerine genel bakış.  
  
 [Eski Dil Hizmeti Uygulama](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 MPF kullanarak bir dil hizmetini uygulamak için gerekenleri açıklar.  
  
 [Eski Dil Hizmeti Kaydetme](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 İle MPF tabanlı dil hizmeti kaydetmek için gereken adımları açıklar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Eski Dil Hizmeti Ayrıştırıcısı ve Tarayıcısı](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 MPF kullanarak bir dil hizmetinin tüm özelliklerini uygulamak için gereken iki ayrıştırıcıları açıklar.  
  
 [İzlenecek yol: Eski Dil Hizmeti oluşturma](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 Bir VSPackage içinde MPF dil hizmeti uygulamak için gereken temel adımları sağlar.  
  
 [İzlenecek yol: Yüklü Kod Parçacıklarının Listesini Alma (Eski Uygulama)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 Yüklü kod parçacıklarının listesini alma tekniklerini gösterir.  
  
 [Eski Dil Hizmeti Özellikleri](../../extensibility/internals/legacy-language-service-features1.md)  
 MPF kullanarak bir dil hizmetinin tüm özelliklerini uygulamak için ne yapılması gerektiğini ayrıntılarıyla belirten konuların bağlantılarını sağlar.
