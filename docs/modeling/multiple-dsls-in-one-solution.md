---
title: Bir Çözümde Birden Çok DSL
description: Birden fazla etki alanına özgü dili (DSL) tek bir çözümün parçası olarak paketleyebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11baf6439062e28c7361e2fabb4dea4a3430f237
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390925"
---
# <a name="multiple-dsls-in-one-solution"></a>Bir Çözümde Birden Çok DSL

Birlikte yüklenmeleri için tek bir çözümün parçası olarak çeşitli DSL'leri paketliysiniz.

Birden çok DSL'i tümleştiren çeşitli teknikler kullanabilirsiniz. Daha fazla bilgi için [bkz. Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) kullanarak Modelleri Tümleştirme ve Nasıl [Musunuz? Sürükle ve](../modeling/how-to-add-a-drag-and-drop-handler.md) Bırak İşleyicisi Ekleme ve [Kopyalama Davranışını Özelleştirme.](../modeling/customizing-copy-behavior.md)

## <a name="build-more-than-one-dsl-in-the-same-solution"></a>Aynı çözümde birden fazla DSL oluşturma

1. Yeni bir **VSIX Projesi projesi** oluşturun.

2. VSIX çözüm dizininde iki veya daha fazla DSL projesi oluşturun.

   - Her DSL için yeni bir Visual Studio. Yeni DSL'i oluşturun ve VSIX çözümüyle aynı çözüm klasörünü belirtin.

   - Her DSL'i farklı bir dosya adı uzantısıyla oluşturduklardan emin olun.

   - **Dsl** ve **DslPackage projelerinin adlarını,** hepsinin farklı olacak şekilde değiştirme. Örneğin: `Dsl1` , `DslPackage1` , , `Dsl2` `DslPackage2` .

   - Her **DslPackage \* \source.extension.tt** içinde, bu satırı doğru Dsl proje adıyla güncelleştirin:

      `string dslProjectName = "Dsl2";`

   - VSIX çözümünde Dsl* ve DslPackage projelerini \* ekleyin. Her çifti kendi çözüm klasörüne yer almak istiyor olabilir.

2. DSL'lerin VSIX bildirimlerini birleştirin:

   1. _YourVsixProject_**\source.extension.manifest'i açın.**

   2. Her DSL için İçerik **Ekle'yi seçin ve** şunları ekleyin:

       - `Dsl*`**MEF** Bileşeni olarak proje

       - `DslPackage*`**MEF** Bileşeni olarak proje

       - `DslPackage*` VS Paketi **olarak proje**

3. Çözümü derleyin.

   Sonuçta elde edilen VSIX her iki DSL'i de yükleyecek. F5 kullanarak bunları test edin veya _YourVsixProject_**\bin\Debug \\ \* .vsix dağıtın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)