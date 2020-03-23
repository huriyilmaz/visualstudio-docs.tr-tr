---
title: Seçenekler, Metin Editörü, JavaScript, Proje
ms.date: 1/15/2019
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 190cbdb2a8096415985d83fc525b997572d252c2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68605920"
---
# <a name="options-text-editor-javascript-project"></a>Seçenekler, Metin Editörü, JavaScript, Proje

Kod Düzenleyicisi'nde JavaScript ve TypeScript proje seçeneklerini belirtmek için **Seçenekler** iletişim kutusunun **Proje** sayfasını kullanın. Bu sayfaya erişmek için menü çubuğunda **Araçlar** > **Seçenekleri'ni**seçin ve ardından **Text Editor** > **JavaScript/TypeScript** > **Project'i**genişletin.

## <a name="project-analysis-options"></a>Proje Analizi Seçenekleri

Bu seçenekler, düzenleyicinin projeleri nasıl analiz edebildiğini, tanılamayı nasıl raporladığını ve iyileştirmeler önerdiğini belirler. Düzenleyicinin bu durumları nasıl ele adadığını belirtmek için seçenekleri seçin veya temizleyin.

### <a name="uielement-list"></a>UIElement listesi

- **Yalnızca düzenleyicide açılan dosyaları içeren projeleri çözümleme**
- **Yalnızca düzenleyicide açılan dosyalar için tanılama yı bildirme**
- **Düzeltme olmayan olası iyileştirmeler önerin**

## <a name="virtual-projects-in-solution-explorer"></a>Çözüm Gezgini'nde Sanal Projeler

Bu seçenekler, Bir Çözüm yüklendiğinde veya yüklenmediğinde Sanal Projeler'i görüntüleyip görüntülemeyeceğinizi seçmenize olanak tanır.

## <a name="compile-on-save"></a>Kaydet'te derleme

Bu seçenekler, projenin parçası olmayan TypeScript dosyalarının otomatik olarak derlenip derlenmediğini belirler. Onay kutusunu seçin ve ardından kullanılacak kod oluşturma türünü seçin.

### <a name="uielement-list"></a>UIElement listesi

- **Projenin parçası olmayan modüller için AMD kod oluşturma yı kullanma**
- **Projenin parçası olmayan modüller için CommonJS kod oluşturma yı kullanma**
- **Projenin parçası olmayan modüller için UMD kod oluşturma yı kullanma**
- **Projenin parçası olmayan modüller için Sistem kodu oluşturmayı kullanma**
- **Projenin parçası olmayan modüller için ES2015 kod oluşturma yı kullanma**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Projenin parçası olmayan dosyalar için ECMAScript sürümü

Bu seçenekler, projenin parçası olmayan dosyalar için ECMAScript sürümünü seçmenize olanak tanır. **ECMAScript 3, ECMAScript** **5**veya **ECMAScript 6**arasında seçim yapabilirsiniz.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>Projenin parçası olmayan TSX dosyaları için JSX Emit

Bu seçenekler, düzenleyicinin projenin parçası olmayan TypeScript dosyalarını nasıl ele adadığını belirler.

### <a name="uielement-list"></a>UIElement listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Tepki Çerçevesi**|Bu seçenek seçildiğinde, Kod Düzenleyicisi *bir .js* dosya uzantısı yayır.|
|**Korumak**|Bu seçenek seçildiğinde, Kod Düzenleyicisi JSX'i çıktının bir parçası olarak tutar ve *.jsx* dosya uzantısı yayır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)