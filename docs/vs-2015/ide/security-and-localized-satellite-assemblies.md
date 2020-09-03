---
title: Güvenlik ve yerelleştirilmiş uydu derlemeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- key pairs for strong-named assemblies
- strong-named assemblies, security considerations
- satellite assemblies, localized
- code signing, assemblies
- security [Visual Studio], assemblies
- strong-named assemblies, localized
- assemblies [Visual Studio], security
- localization, satellite assemblies
ms.assetid: 6d953840-b301-47d5-8d34-30c1b29b5071
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 866e313a36af5ef72f910a5eafbf7b31c971d890
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672908"
---
# <a name="security-and-localized-satellite-assemblies"></a>Güvenlik ve Yerleştirilmiş Yardımcı Derlemeler
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ana derlemeleriniz tanımlayıcı adlandırma kullanıyorsa, uydu derlemelerinin ana derlemeyle aynı özel anahtarla imzalanması gerekir. Ortak/özel anahtar çifti, ana ve uydu Derlemeleriyle eşleşmezse, kaynaklarınız yüklenmez. Derlemeleri imzalama hakkında daha fazla bilgi için bkz. [nasıl yapılır: derlemeyi güçlü bir adla imzalama](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67).

 Genel olarak, kuruluşunuzun imzalama grubuna veya bir dış imzalama kuruluşuna özel anahtarla oturum açmanız gerekebilir. Bunun nedeni özel anahtarın hassas doğası gereği: erişim genellikle birkaç bireyle kısıtlıdır. Geliştirme sırasında gecikmeli imzalamayı kullanabilirsiniz. Daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](https://msdn.microsoft.com/library/9d300e17-5bf1-4360-97da-2aa55efd9070).

## <a name="see-also"></a>Ayrıca Bkz.
 [Bütünleştirilmiş kod güvenliği önemli noktaları](https://msdn.microsoft.com/library/1b5439c1-f3d5-4529-bd69-01814703d067) temel [güvenlik kavramları](https://msdn.microsoft.com/library/3cfced4f-ea02-4e66-ae98-d69286363e98) uygulamalar, uygulamaları [genelleştirmek ve yerelleştirme](../ide/globalizing-and-localizing-applications.md) uygulamaları [.NET Framework temel alınarak uluslararası uygulamalara giriş](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md) [Localizing Applications](../ide/localizing-applications.md)
