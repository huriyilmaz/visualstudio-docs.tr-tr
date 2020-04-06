---
title: EditorConfig'i desteklemek için dil hizmetini genişletin
ms.date: 11/22/2017
ms.topic: conceptual
helpviewer_keywords:
- editorconfig [extensibility]
- editorconfig, supporting in a language service
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddfe0e30904d000b4fd70c85371d29a2ee486932
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699579"
---
# <a name="supporting-editorconfig-for-your-language-service"></a>Dil hizmetiniz için EditorConfig'i destekleme

[EditorConfig](https://editorconfig.org/) dosyaları, girinti boyut gibi ortak metin düzenleyicisi seçeneklerini proje başına olarak açıklamanızı sağlar. Visual Studio'nun EditorConfig dosyaları desteği hakkında daha fazla bilgi edinmek için [EditorConfig'i kullanarak taşınabilir düzenleyici ayarlarını oluştur'a](../ide/create-portable-custom-editor-options.md)bakın.

Çoğu durumda Visual Studio dil hizmeti uyguladığınızda, EditorConfig evrensel özelliklerini desteklemek için ek bir çalışma gerekmez. Çekirdek düzenleyici, kullanıcılar dosyaları açtığında .editorconfig dosyasını otomatik olarak keşfeder ve okur ve uygun metin arabelleği ve görünüm seçeneklerini ayarlar. Ancak, sekmeler ve boşluklar gibi yapılan lar için, bazı dil hizmetleri genel ayarları kullanmak yerine uygun bağlamsal metin görünümü seçeneğini kullanmayı tercih eder. Bu gibi durumlarda, dil hizmeti EditorConfig dosyalarını desteklemek için güncelleştirilmelidir.

Genel dile _özgü_ bir seçeneği _bağlamsal_ bir seçenekle değiştirerek, EditorConfig dosyalarını desteklemek için bir dil hizmetini güncelleştirmek için gereken değişiklikler şunlardır:

## <a name="indent-style"></a>Girintisi stili

Dile özel seçenekler | Bağlamsal seçenekler
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.fInsertTabs<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs|!textBufferOptions.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)<br/>!textView.Options.GetOptionValue(DefaultOptions.ConvertTabsToSpacesOptionId)

## <a name="indent-size"></a>Girintisi boyutu

Dile özel seçenekler | Bağlamsal seçenekler
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uIndentSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.IndentSize|textBufferOptions.GetOptionValue(DefaultOptions.IndentSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.IndentSizeOptionId)

## <a name="tab-size"></a>Sekme boyutu

Dile özel seçenekler | Bağlamsal seçenekler
-------|--------
Microsoft.VisualStudio.TextManager.Interop.LANGPREFERENCES.uTabSize<br/>Microsoft.VisualStudio.Package.LanguagePreferences.InsertTabs.TabSize|textBufferOptions.GetOptionValue(DefaultOptions.TabSizeOptionId)<br/>textView.Options.GetOptionValue(DefaultOptions.TabSizeOptionId)

## <a name="see-also"></a>Ayrıca bkz.

- [EditorConfig'i kullanarak taşınabilir düzenleyici ayarları oluşturma](../ide/create-portable-custom-editor-options.md)
- [Editör ve dil hizmetlerinin genişletilmesi](../extensibility/extending-the-editor-and-language-services.md)
