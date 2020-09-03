---
title: Seçenekler, metin düzenleyici, HTML (Web Forms), doğrulama
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568288"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Seçenekler, metin düzenleyici, HTML (Web Forms), doğrulama

HTML düzenleyicisinin belgenizde HTML biçimlendirme sözdizimini nasıl denetleyeceğini gösteren tercihleri ayarlamak için **doğrulama** seçenekleri sayfasını kullanın. Bu sayfaya erişmek için, menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin ve ardından **metin Düzenleyicisi**  >  **HTML (Web Forms)**  >  **doğrulaması**' nı genişletin.

## <a name="validation"></a>Doğrulama

- **Doğrulama şeması algılaması için DOCTYPE kullanın**

   Şema, bu şemada hangi öğelerin, özniteliklerin ve büyük/küçük harflerin geçerli olduğunu belirler. IntelliSense 'de kullanılabilen etiketleri ve öznitelikleri de belirler.

   Visual Studio 'nun sayfa< içeriğini kullanmasını istiyorsanız bu seçeneği belirleyin ** ! ** Şemayı öğrenmek IÇIN DOCTYPE>bildirimi ve **HTML** öğesi. Örneğin, bu seçeneği belirlerseniz ve sayfada bildirim varsa `<!DOCTYPE html>` , Visual STUDIO HTML5 şemasını kullanır. Ancak, **HTML** etiketinde, gibi bir **xmlns** özniteliği varsa `<html xmlns="http://www.w3.org/1999/xhtml">` , Visual Studio XHTML5 şemasını kullanır.

- **Hiçbir DOCTYPE bulunamadığında hedefle**

   < olmadığında doğrulanacak şemayı seçin ** ! Sayfada DOCTYPE>** bildirimi.

  - **Hataları göster**

     Doğrulamayı etkinleştirmek için onay kutusunu işaretleyin. Onay kutusu seçili değilse, düzenleyici doğrulama hatalarını işaretlemez.

     Diğer onay kutuları, düzenleyicinin işaretlemesini istediğiniz bağımsız hata türlerini belirterek doğrulamayı hassas bir şekilde ayarlamanıza olanak sağlar.

     > [!NOTE]
     > Bazı şemalar, ayrı hata türlerini işaretlemek için seçenek sunmaz. Örneğin, hedef şema olarak **XHTML 1,1** ' i seçerseniz, tüm seçenek onay kutuları devre dışıdır. Bu örnekte, tüm hata türleri işaretlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
