---
title: Tek bir çözümde birden çok DSLs | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9a3b35e05108db879b365b9cafc39cacdf843397
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668562"
---
# <a name="multiple-dsls-in-one-solution"></a>Bir Çözümde Birden Çok DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Birden çok DSLs 'yi tek bir çözümün parçası olarak paketleyebilir, böylece birlikte yüklenirler.

 Birden çok DSLs 'yi bütünleştirmek için birkaç teknik kullanabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio ModelBus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md) ve [nasıl yapılır: sürükle ve bırak Işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md) ve [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Aynı çözümde birden fazla DSL oluşturmak için

1. İki veya daha fazla DSL çözümü ve bir VSıX projesi oluşturun ve tüm projeleri tek bir çözüme ekleyin.

   - Yeni bir VSIX projesi oluşturmak için: **Yeni proje** iletişim kutusunda, **görsel C#** , **genişletilebilirlik**, **VSIX projesi**' ni seçin.

   - VSıX çözüm dizininde iki veya daha fazla DSL çözümü oluşturun.

        Her DSL için, Visual Studio 'nun yeni bir örneğini açın. Yeni DSL 'yi oluşturun ve VSıX çözümüyle aynı çözüm klasörünü belirtin.

        Her bir DSL 'yi farklı bir dosya adı uzantısıyla oluşturduğunuzdan emin olun.

   - **DSL** ve **DslPackage** projelerinin adlarını farklı olacak şekilde değiştirin. Örneğin: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   - Her **DslPackage \* \ Source.Extension.tt**, bu satırı doğru DSL projesi adına güncelleştirin:

        `string dslProjectName = "Dsl2";`

   - VSıX çözümünde DSL * ve DslPackage \* projelerini ekleyin.

        Her çifti kendi çözüm klasörüne yerleştirmek isteyebilirsiniz.

2. DSLs 'lerin VSıX bildirimlerini birleştirin:

   1. _Yourvaltıproject_ **\Source.Extension.manifest**açın.

   2. Her DSL için **Içerik Ekle** ve Ekle ' yi seçin:

       - bir **MEF bileşeni** olarak proje `Dsl*`

       - bir **MEF bileşeni** olarak proje `DslPackage*`

       - projeyi **vs paketi** olarak `DslPackage*`

3. Çözümü oluşturun.

   Elde edilen VSıX her iki DSLs 'i de yükleyecek. F5 'i kullanarak bunları test edebilir veya **\\ \*. vsix**' _yi dağıtabilirsiniz._

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio ModelBus Ile modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [: sürükle ve bırak Işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md) [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md)
