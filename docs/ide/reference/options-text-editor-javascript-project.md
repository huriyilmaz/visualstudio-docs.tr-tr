---
title: Seçenekler, metin düzenleyici, JavaScript, proje
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6e4f5ff4e1081bbbe6aced4465afb40318048a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85285367"
---
# <a name="options-text-editor-javascript-project"></a>Seçenekler, metin düzenleyici, JavaScript, proje

Kod düzenleyicisinde JavaScript ve TypeScript proje seçeneklerini belirtmek için **Seçenekler** Iletişim kutusunun **Proje** sayfasını kullanın. Bu sayfaya erişmek için, menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin ve ardından **metin düzenleyici**  >  **JavaScript/TypeScript**  >  **projesi**' ni genişletin.

## <a name="project-analysis-options"></a>Proje Analizi Seçenekleri

Bu seçenekler, düzenleyicinin projeleri nasıl analiz eder, tanılama raporlar ve iyileştirmeler önerir. Düzenleyicinin bu durumları nasıl işleyeceğini belirlemek için seçenekleri seçin veya temizleyin.

### <a name="uielement-list"></a>UIElement listesi

- **Yalnızca düzenleyicide açılan dosyalar içeren projeleri analiz et**
- **Yalnızca düzenleyicide açılan dosyalar için tanılamayı raporla**
- **Düzeltme olmayan olası iyileştirmeler önerin**

## <a name="virtual-projects-in-solution-explorer"></a>Çözüm Gezgini sanal projeler

Bu seçenekler, bir çözüm yüklendiğinde veya yüklü olmadığında sanal projelerin görüntülenip görüntülenmeyeceğini seçmenizi sağlar.

## <a name="compile-on-save"></a>Kaydetme sırasında derle

Bu seçenekler, projenin parçası olmayan TypeScript dosyalarının otomatik olarak derlenip derlenmediğini belirtir. Visual Studio, *C:\Program Files (x86) \Microsoft SDKs\TypeScript*' de yüklü olan TypeScript 'in en son sürümünü kullanarak derlenir.

Onay kutusunu seçin ve ardından kullanılacak kod oluşturma türünü seçin.

### <a name="uielement-list"></a>UIElement listesi

- **Projenin parçası olmayan modüller için AMD kod üretimi kullanma**
- **Projenin parçası olmayan modüller için CommonJS kod üretimini kullanın**
- **Projenin parçası olmayan modüller için UMD kod üretimini kullanın**
- **Projenin parçası olmayan modüller için sistem kodu oluşturmayı kullanma**
- **Projenin parçası olmayan modüller için ES2015 kod oluşturmayı kullanma**

## <a name="ecmascript-version-for-files-that-are-not-part-of-a-project"></a>Bir projenin parçası olmayan dosyalar için ECMAScript sürümü

Bu seçenekler, bir projenin parçası olmayan dosyalar için ECMAScript sürümünü seçmenizi sağlar. **ECMAScript 3**, **ECMAScript 5**veya **ECMAScript 6**arasında seçim yapabilirsiniz.

## <a name="jsx-emit-for-tsx-files-that-are-not-part-of-a-project"></a>Projenin parçası olmayan TSX dosyaları için JSX yayma

Bu seçenekler, düzenleyicinin bir projenin parçası olmayan TypeScript dosyalarını nasıl ele aldığını tespit eder.

### <a name="uielement-list"></a>UIElement listesi

|Seçenek|Açıklama|
|------------|-----------------|
|**Tepki verme çerçevesi**|Bu seçenek belirlendiğinde, kod Düzenleyicisi bir *. js* dosya uzantısı yayar.|
|**Koruyup**|Bu seçenek belirlendiğinde, kod Düzenleyicisi, JSX 'in çıktının bir parçası olarak devam eder ve bir *. JSX* dosya uzantısını yayar.|

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)