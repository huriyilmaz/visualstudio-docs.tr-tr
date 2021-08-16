---
title: Seçenekler, Metin Düzenleyici, HTML (Web Forms), Doğrulama
description: HTML düzenleyicisinin belgeniz içinde HTML işaretleme söz dizimini nasıl kontrol etmek istediğinize göre tercihleri ayarlamak için HTML bölümündeki Doğrulama sayfasını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 1/15/2019
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.HTML.Validation
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9266872ef9535802f66d3b068a3f10d51f4270d59de349f53b6547bf79a5afb7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121412224"
---
# <a name="options-text-editor-html-web-forms-validation"></a>Seçenekler, Metin Düzenleyici, HTML (Web Forms), Doğrulama

DOĞRULAMA seçenekleri **sayfasını** kullanarak HTML düzenleyicisinin belgeniz içinde HTML işaretleme söz dizimini nasıl denetler? Bu sayfaya erişmek için, menü çubuğunda Araçlar Seçenekleri'ni seçin ve ardından Metin  >  Düzenleyicisi   >  **HTML (Web Forms) Doğrulama'ya**  >  **genişletin.**

## <a name="validation"></a>Doğrulama

- **Doğrulama şeması algılama için doctype kullanma**

   Şema, bu şemada hangi öğelerin, özniteliklerin ve büyük/küçük harfle ifadelerin geçerli olduğunu belirler. Ayrıca IntelliSense'te kullanılabilen etiketleri ve öznitelikleri de belirler.

   Sayfanın içeriğini kullanmak Visual Studio için bu seçeneği **<! DOCTYPE>** belirlemek için bildirim ve **html** öğesi kullanır. Örneğin, bu seçeneği belirtirseniz ve sayfada bildirimi `<!DOCTYPE html>` varsa, Visual Studio HTML5 şemasını kullanır. Ancak, **html etiketi** gibi bir **xmlns** özniteliğine `<html xmlns="http://www.w3.org/1999/xhtml">` sahipse, Visual Studio XHTML5 şemasını kullanır.

- **Doctype bulunamaysa hedef**

   Herhangi bir sorun olduğunda doğrulanması gereken **şemayı<! DOCTYPE>** bildirimini gösterir.

  - **Hataları göster**

     Doğrulamayı etkinleştirmek için onay kutusunu seçin. Onay kutusu seçili değilse düzenleyici doğrulama hatalarını işaretlemez.

     Diğer onay kutuları, düzenleyicinin işaretlemek istediğiniz hata türlerini belirterek doğrulamada ince ayara sahip olur.

     > [!NOTE]
     > Bazı şemalar, tek tek hata türlerini işaretleme seçenekleri sunmaz. Örneğin, hedef şema olarak **XHTML 1.1'i** seçerseniz tüm seçenek onay kutuları devre dışı bırakılır. Bu örnekte, tüm hata türleri işaretlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Genel, Ortam, Seçenekler İletişim Kutusu](../../ide/reference/general-environment-options-dialog-box.md)
