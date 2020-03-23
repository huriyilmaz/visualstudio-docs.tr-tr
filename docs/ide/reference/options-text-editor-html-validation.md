---
title: Seçenekler, Metin Düzenleyicisi, HTML (Web Formları), Doğrulama
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ede4600cb1fa1df118b4635a193d8bff348d5119
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568288"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Seçenekler, Metin Düzenleyicisi, HTML (Web Formları), Doğrulama

HTML düzenleyicisinin belgenizdeki HTML biçimlendirmesözdizimini nasıl denetlediğine yönelik tercihleri ayarlamak için **Doğrulama** seçenekleri sayfasını kullanın. Bu sayfaya erişmek için menü çubuğunda **Araçlar** > **Seçenekleri'ni**seçin ve ardından **Metin Düzenleyicisi** > **HTML (Web Formları)** > **Doğrulama'yı**genişletin.

## <a name="validation"></a>Doğrulama

- **Doğrulama şeması algılaması için doctype kullanın**

   Şema, bu şemada hangi öğelerin, özniteliklerin ve büyük harflerin geçerli olduğunu belirler. Ayrıca, IntelliSense'de kullanılabilen etiketleri ve öznitelikleri belirler.

   Visual Studio'nun sayfanın< içeriğini kullanmasını istiyorsanız bu seçeneği **belirleyin! DOCTYPE>** bildirimi ve **html** öğesi şemayı belirlemek için. Örneğin, bu seçeneği seçerseniz ve sayfada `<!DOCTYPE html>`bildirim varsa, Visual Studio HTML5 şemasını kullanır. Ancak, **html** etiketi gibi bir **xmlns** özniteliği `<html xmlns="http://www.w3.org/1999/xhtml">`varsa, Visual Studio XHTML5 şema kullanır.

- **Doküman türü bulunamadığınızda hedef**

   hiçbir< olmadığında karşı doğrulamak için şema **seçin! DOCTYPE**>bildirimi sayfada.

  - **Hataları göster**

     Doğrulamayı etkinleştirmek için onay kutusunu seçin. Onay kutusu seçili değilse, düzenleyici doğrulama hatalarını işaretlemez.

     Diğer onay kutuları, düzenleyicinin işaretlemesini istediğiniz tek tek hata türlerini belirterek doğrulamada ince ayar lamanızı sağlar.

     > [!NOTE]
     > Bazı şemalar, tek tek hata türlerini işaretleme seçenekleri sunmaz. Örneğin, hedef şema olarak **XHTML 1.1'i** seçerseniz, tüm seçenek onay kutuları devre dışı bırakılır. Bu durumda, tüm hata türleri işaretlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
