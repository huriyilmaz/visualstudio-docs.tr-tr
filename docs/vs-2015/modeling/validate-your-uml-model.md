---
title: UML modelinizi doğrulama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML, constraints
- UML, validation
ms.assetid: deed5092-c11d-4431-a801-1e866a103075
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8dfaf19e358d96b7737b06880d6fa4581b5c54f8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659367"
---
# <a name="validate-your-uml-model"></a>UML modelinizi doğrulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 'da çizeceğiniz bazı UML modelleriniz projenizde geçersiz olarak kabul edilebilir. Örneğin, kullanım durumunun aktörleri temsil eden Yaşam çizgilerinin bulunduğu bir dizi diyagramına her zaman bir kullanım örneğinin bağlı olması gerekebilir. Takımınızın bu gibi gereksinimlere uyum sağlamak için *kısıtlamalar* yükleyebilir veya tanımlayabilirsiniz. Kullanıcı bir modeli kaydettiğinde veya açtığında kısıtlamalar uygulanabilir ve menü komutu tarafından çağrılabilir.

 @No__t_0, takımınızın UML modellerini nasıl yorumlayacağını ve kullandığını bağlı olduklarından, hiçbir kısıtlama sağlanmaz. Ancak kendi kısıtlamalarınızı tanımlayabilir ve diğer kullanıcılar tarafından tanımlanan kısıtlamaları yükleyebilirsiniz. Kısıtlamaların nasıl tanımlanacağını ve dağıtım için nasıl paketleyeceğinizi öğrenmek için bkz. [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="invoking-validation"></a>Doğrulama çağrılıyor
 Bir doğrulama uzantısı yüklediğinizde, sağladığı kısıtlamalar aşağıdaki durumlarda uygulanabilir. Bazı kısıtlamalar bu durumların yalnızca bazılarında uygulanmak üzere ayarlanır.

- **Doğrulama komutu.** Doğrulama 'yı dilediğiniz zaman çağırmak için **mimari** menüsünde **UML modelini doğrula** ' ya tıklayın.

  > [!NOTE]
  > Komut yalnızca doğrulama kısıtlamaları yüklüyse görüntülenir.

- **Model kaydetme sırasında.** Modeli kaydettiğinizde doğrulama kısıtlamaları uygulanabilir. Bu kısıtlamaların amacı, projenizin yorumuna göre geçersiz bir modeli kaydettiğinizden emin olmanıza yardımcı olur.

   Hatalar varsa, yine de modeli kaydetmek isteyip istemediğiniz sorulur. Hataları düzeltmeyi veya yine de modeli kaydetmeyi seçebilirsiniz.

- **Bir model açılırken.** Bir modeli açtığınızda, modeli kaydettiğinizde varolan hata iletilerini geri yüklemek için doğrulama yöntemleri uygulanabilir. Hatalar, bir modelin farklı bölümlerinde çalışan kullanıcılar tarafından yapılan değişiklikler arasındaki tutarsızlıklar tarafından da sunulabilir. Daha fazla bilgi için bkz. [model paylaşma ve diyagramları dışarı aktarma](../modeling/share-models-and-exporting-diagrams.md).

  Doğrulama hataları [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hataları penceresinde raporlanır.

  Diyagramda yanlış olan öğeleri seçmek için hataya çift tıklayın. Bu, yalnızca yanlış öğeler açık diyagramda görünür durumdaysa işe yarar.

## <a name="installing-validation-constraints"></a>Doğrulama kısıtlamalarını yükleme
 Kısıtlamalar [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Extension (VSıX) dosyaları içinde paketlenmiştir. Genellikle, bir dizi kısıtlama, menü komutları, profiller ve araç kutusu öğeleri gibi diğer tanımları da içeren bir uzantının parçası olacaktır.

#### <a name="to-install-a-visual-studio-extension"></a>Visual Studio uzantısı yüklemek için

1. Windows Gezgini 'nde (veya dosya Gezgini) **. vsix** dosyasına çift tıklayın.

2. Zaten çalışmakta olan tüm [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] örneklerini yeniden başlatın.

## <a name="disabling-and-uninstalling-validation-constraints"></a>Doğrulama kısıtlamalarını devre dışı bırakma ve kaldırma
 Kısıtlamaların uygulanamadığı bir modelle çalışmak istediğinizde, bunları içeren uzantıyı geçici olarak devre dışı bırakabilirsiniz. Bu şekilde, farklı türlerde modellerle farklı şekillerde çalışarak farklı uzantıları etkinleştirip devre dışı bırakabilirsiniz.

#### <a name="to-disable-or-uninstall-a-visual-studio-extension"></a>Bir Visual Studio uzantısını devre dışı bırakmak veya kaldırmak için

1. @No__t_0 **araçları** menüsünde **Uzantılar ve güncelleştirmeler**' e tıklayın.

2. Uzantının yanında, uzantıyı geçici olarak devre dışı bırakmak için **devre dışı bırak** seçeneğine tıklayın. Daha sonra **Uzantılar ve güncelleştirmeler** penceresine dönerek yeniden etkinleştirebilirsiniz.

     \- veya-

     Uzantıyı kaldırmak için **Kaldır** ' a tıklayın.

3. @No__t_0 yeniden başlatın.

## <a name="see-also"></a>Ayrıca Bkz.
 [UML modelleri için doğrulama kısıtlamaları tanımlama](../modeling/define-validation-constraints-for-uml-models.md) uygulama [geliştirme sürecinizdeki](../modeling/use-models-in-your-development-process.md) [modelleriniz için model oluşturma](../modeling/create-models-for-your-app.md)
