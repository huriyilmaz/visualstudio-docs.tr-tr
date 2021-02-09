---
title: Dil hizmetini, EditorConfig 'i destekleyecek şekilde Genişlet
description: EditorConfig dosyalarını desteklemek üzere bir dil hizmetini güncelleştirmek için yapılacak değişiklikler hakkında bilgi edinin. Genel dile özgü seçeneği bağlamsal seçenekle değiştirin.
ms.custom: SEO-VS-2020
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8ddd7e0c7c1e2655f08b7b7113f43e14bbb37584
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914958"
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
