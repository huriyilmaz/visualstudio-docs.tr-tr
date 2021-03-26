---
title: Dil hizmetini, EditorConfig 'i destekleyecek şekilde Genişlet
description: EditorConfig dosyalarını desteklemek üzere bir dil hizmetini güncelleştirmek için yapılacak değişiklikler hakkında bilgi edinin. Genel dile özgü seçeneği bağlamsal seçenekle değiştirin.
ms.custom: SEO-VS-2020
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3754c40ec1142684b5041341b22035eaec06ec8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105056265"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Dil hizmetiniz için EditorConfig 'i destekleme

[Editorconfig](https://editorconfig.org/) dosyaları, girinti boyutu gibi ortak metin düzenleyicisi seçeneklerini proje başına temelinde açıklamanıza olanak sağlar. Visual Studio 'nun EditorConfig dosyaları desteği hakkında daha fazla bilgi edinmek için bkz. [editorconfig kullanarak taşınabilir düzenleyici ayarları oluşturma](../ide/create-portable-custom-editor-options.md).

Çoğu durumda, Visual Studio Language hizmetini uyguladığınızda, EditorConfig Universal özelliklerini desteklemek için ek bir iş gerekmez. Çekirdek Düzenleyici, kullanıcılar dosyaları açtıklarında. editorconfig dosyasını otomatik olarak bulur ve okur ve uygun metin arabelleğini ve görüntüleme seçeneklerini ayarlar. Ancak, sekmeler ve boşluklar gibi düzenlemeler için, bazı dil Hizmetleri Genel ayarları kullanmak yerine uygun bağlamsal metin görünümü seçeneğini kullanmayı tercih edebilir. Bu durumlarda, dil hizmetinin EditorConfig dosyalarını desteklemesi için güncelleştirilmeleri gerekir.

Aşağıda, genel _dile özgü_ bir seçeneği _bağlamsal_ seçenekle değiştirerek, editorconfig dosyalarını desteklemek üzere bir dil hizmetini güncelleştirmek için gereken değişiklikler aşağıda verilmiştir:

## <a name="indent-style"></a>Girinti stili

Dile özgü seçenekler | Bağlamsal seçenekler
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. fInsertTabs<br/>Microsoft. VisualStudio. Package. LanguagePreferences. ınsertsekmeleri|! textBufferOptions. GetOptionValue (DefaultOptions. Converttabstospacesoptionıd)<br/>! textView. Options. GetOptionValue (DefaultOptions. Converttabstospacesoptionıd)

## <a name="indent-size"></a>Boyut Girintile

Dile özgü seçenekler | Bağlamsal seçenekler
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. Ugirintileme tsize<br/>Microsoft. VisualStudio. Package. LanguagePreferences. InsertTab. girintileme tsize|textBufferOptions. GetOptionValue (DefaultOptions. ınttrsizeoptionıd)<br/>textView. Options. GetOptionValue (DefaultOptions. ınttrsizeoptionıd)

## <a name="tab-size"></a>Sekme boyutu

Dile özgü seçenekler | Bağlamsal seçenekler
-------|--------
Microsoft. VisualStudio. TextManager. Interop. LANGPREFERENCES. Uıtabsize<br/>Microsoft. VisualStudio. Package. LanguagePreferences. InsertTab. TabSize|textBufferOptions. GetOptionValue (DefaultOptions. Tabsizeoptionıd)<br/>textView. Options. GetOptionValue (DefaultOptions. Tabsizeoptionıd)

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig kullanarak taşınabilir düzenleyici ayarları oluşturma](../ide/create-portable-custom-editor-options.md)
- [Düzenleyici ve dil hizmetlerini genişletme](../extensibility/extending-the-editor-and-language-services.md)
