---
title: Bir Çözümde Birden Çok DSL
description: Tek bir çözümün bir parçası olarak, etki alanına özgü birkaç dili (DSLs) birlikte yüklenmek üzere nasıl paketleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d26d321f93d3d70300c8bdfaa758ec87309840bd8d21db3341a5cf7e2040505d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121231528"
---
# <a name="multiple-dsls-in-one-solution"></a>Bir Çözümde Birden Çok DSL

Birden çok DSLs 'yi tek bir çözümün parçası olarak paketleyebilir, böylece birlikte yüklenirler.

Birden çok DSLs 'yi bütünleştirmek için birkaç teknik kullanabilirsiniz. daha fazla bilgi için bkz. [Visual Studio Modelbus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md) ve [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md) ve [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Aynı çözümde birden fazla DSL oluşturun

1. Yeni bir **vsıx Project** projesi oluşturun.

2. VSıX çözüm dizininde iki veya daha fazla DSL projesi oluşturun.

   - Her DSL için Visual Studio yeni bir örneğini açın. Yeni DSL 'yi oluşturun ve VSıX çözümüyle aynı çözüm klasörünü belirtin.

   - Her bir DSL 'yi farklı bir dosya adı uzantısıyla oluşturduğunuzdan emin olun.

   - **DSL** ve **DslPackage** projelerinin adlarını farklı olacak şekilde değiştirin. Örneğin: `Dsl1` ,, `DslPackage1` `Dsl2` , `DslPackage2` .

   - Her **DslPackage \* \ Source.Extension.tt** içinde, bu satırı doğru DSL projesi adına güncelleştirin:

      `string dslProjectName = "Dsl2";`

   - VSıX çözümünde DSL * ve DslPackage \* projelerini ekleyin. Her çifti kendi çözüm klasörüne yerleştirmek isteyebilirsiniz.

2. DSLs 'lerin VSıX bildirimlerini birleştirin:

   1. _Yourvaltıproject_**\Source.Extension.manifest** açın.

   2. Her DSL için **Içerik Ekle** ve Ekle ' yi seçin:

       - `Dsl*`**MEF bileşeni** olarak proje

       - `DslPackage*`**MEF bileşeni** olarak proje

       - `DslPackage*`**vs paketi** olarak proje

3. Çözümü derleyin.

   Elde edilen VSıX her iki DSLs 'i de yükleyecek. F5 'i kullanarak bunları test edebilir veya _Yourvaltproject_**\Bin\Debug \\ \* . vsix**' yi dağıtabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)