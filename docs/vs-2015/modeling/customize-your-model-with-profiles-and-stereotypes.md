---
title: Modelinizi Profiller ve Stereotipler ile özelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b634b11418ef2d4220dc4eb07c825b514ab5494c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301199"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Modelinizi profiller ve stereotipler aracılığıyla özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da sınıflar ve bileşenler gibi standart UML model öğelerini belirli amaçlarla özelleştirmek için uyarlayabilirsiniz. Öğenin özellik listesini değiştirebilen bir model öğesine *stereotip* uygulayabilirsiniz. Stereotipler, *profiller*olarak adlandırılan koleksiyonlar içinde tanımlanır.

 Visual Studio 'nun hangi sürümlerinin bu özelliği desteklediğini görmek için bkz. [mimari ve modelleme araçları Için sürüm desteği](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Bir stereotip kullanmak için bir paketi profile bağlarsınız. Bu, profilde tanımlanan stereotipleri paketteki öğelere uygulamanıza olanak sağlar. Bazı profiller Visual Studio ile birlikte yüklenir. Ayrıca, kendi profillerinizi tanımlayabilirsiniz.

 Stereotiplerde bir öğenin Özellikler listesinde stereotipler ayarlanabilir. Diyagramdaki ana şekil türleri için, örnekte gösterildiği gibi, uygulanan stereotipler da şekilde görünür.

 ![Stereotipe sahip UML sınıfı.](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> Model oluşturmak için bir profil kullanır ve ardından modeli başka biriyle paylaşıyorsanız, kendi bilgisayarlarına aynı profili yüklemedikleri takdirde stereotipleri göremez.

## <a name="related-topics"></a>İlgili Konular

|Başlık|Açıklama|
|-----------|-----------------|
|[UML model öğelerine stereotipler ekleme](../modeling/add-stereotypes-to-uml-model-elements.md)|Bir model öğesini bir pakete yerleştirme, paketi bir profile bağlama ve bir stereotipine bir stereotip uygulama.|
|[UML modelleri için standart stereotipler](../modeling/standard-stereotypes-for-uml-models.md)|UML Standart profilleri L2 ve L3, Visual Studio ile yüklenir ve her model varsayılan olarak bunlara bağlanır. Modellerinize açıklama eklemek için kullanabileceğiniz stereotipler sağlar.<br /><br /> Örneğin, yalnızca örneklerinin dışarıdan görünür davranışını tanımlamak için tasarlanan bir sınıfa «Specification» stereotipini uygulayabilirsiniz.|
|[UML’yi genişletmek için profil tanımlama](../modeling/define-a-profile-to-extend-uml.md)|Kendi uygulama alanınızı uyarlanan kendi stereotiplerinizi ve araçlarınızı tanımlayabilirsiniz.<br /><br /> Örneğin, bankacılık yazılımı geliştirirseniz, sınıflara uygulanabilen bir «Account» stereotipi tanımlayabilirsiniz. Daha sonra farklı hesap türlerini ve bunların ilişkilerini betimleyen sınıf diyagramlarını kullanabilirsiniz.|
|[UML profili yükleme](../modeling/install-a-uml-profile.md)|Size bir UML profili verildiyse, bunu bilgisayarınıza yükleyebilirsiniz.|
|[Özel bir modelleme araç kutusu öğesi tanımlama](../modeling/define-a-custom-modeling-toolbox-item.md)|Özel bir araç kutusu öğesi, yeni öğelerde bir stereotipin sürekli olarak ayarlanmasını sağlar.|
