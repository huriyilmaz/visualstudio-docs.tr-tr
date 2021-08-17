---
title: Seçenekler, metin düzenleyici, JavaScript, Project
description: kod düzenleyicisinde JavaScript ve TypeScript proje seçeneklerini belirtmek için seçenekler iletişim kutusunun Project sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 06/19/2020
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Project
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project.General
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Project
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bfd3f621a0d969c7d5ee684a4277ecbf89e633fe2beba34209f07687d002d1e5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121334360"
---
# <a name="options-text-editor-javascript-project"></a>Seçenekler, metin düzenleyici, JavaScript, Project

kod düzenleyicisinde JavaScript ve TypeScript proje seçeneklerini belirtmek için **seçenekler** iletişim kutusunun **Project** sayfasını kullanın. bu sayfaya erişmek için, menü çubuğunda **araçlar**  >  **seçenekler**' i seçin ve ardından **metin düzenleyici**  >  **JavaScript/TypeScript**  >  **Project**' ı genişletin.

## <a name="project-analysis-options"></a>Project Analiz seçenekleri

Bu seçenekler, düzenleyicinin projeleri nasıl analiz eder, tanılama raporlar ve iyileştirmeler önerir. Düzenleyicinin bu durumları nasıl işleyeceğini belirlemek için seçenekleri seçin veya temizleyin.

### <a name="uielement-list"></a>UIElement listesi

- **Yalnızca düzenleyicide açılan dosyalar içeren projeleri analiz et**
- **Yalnızca düzenleyicide açılan dosyalar için tanılamayı raporla**
- **Düzeltme olmayan olası iyileştirmeler önerin**

## <a name="virtual-projects-in-solution-explorer"></a>Çözüm Gezgini sanal projeler

Bu seçenekler, bir çözüm yüklendiğinde veya yüklü olmadığında sanal projelerin görüntülenip görüntülenmeyeceğini seçmenizi sağlar.

## <a name="compile-on-save"></a>Kaydetme sırasında derle

Bu seçenekler, projenin parçası olmayan TypeScript dosyalarının otomatik olarak derlenip derlenmediğini belirtir. Visual Studio, *C:\Program Files (x86) \microsoft sdks\typescript*' de yüklü olan TypeScript 'in en son sürümünü kullanarak derlenir.

Onay kutusunu seçin ve ardından kullanılacak kod oluşturma türünü seçin.

### <a name="uielement-list"></a>UIElement listesi

- **Projenin parçası olmayan modüller için AMD kod üretimi kullanma**
- **Projenin parçası olmayan modüller için CommonJS kod üretimini kullanın**
- **Projenin parçası olmayan modüller için UMD kod üretimini kullanın**
- **Projenin parçası olmayan modüller için sistem kodu oluşturmayı kullanma**
- **Projenin parçası olmayan modüller için ES2015 kod oluşturmayı kullanma**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Bir projenin parçası olmayan dosyalar için ECMAScript sürümü

Bu seçenekler, bir projenin parçası olmayan dosyalar için ECMAScript sürümünü seçmenizi sağlar. **ECMAScript 3**, **ECMAScript 5** veya **ECMAScript 6** arasında seçim yapabilirsiniz.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>Projenin parçası olmayan TSX dosyaları için JSX yayma

Bu seçenekler, düzenleyicinin bir projenin parçası olmayan TypeScript dosyalarını nasıl ele aldığını tespit eder.

### <a name="uielement-list"></a>UIElement listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**React Çerçevenin**|Bu seçenek belirlendiğinde, kod Düzenleyicisi bir *.js* dosya uzantısı yayar.|
|**Koruyup**|Bu seçenek belirlendiğinde, kod Düzenleyicisi, JSX 'in çıktının bir parçası olarak devam eder ve bir *. JSX* dosya uzantısını yayar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)