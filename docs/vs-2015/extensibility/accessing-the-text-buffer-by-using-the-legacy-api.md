---
title: Eski API kullanarak metin arabelleğine erişme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - text buffers
ms.assetid: cd6cf4ae-fff5-4e23-b293-7cbafdb8aed2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f2cfbd84bc4f9298358a2a2d1ba87f76d6e5303c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185001"
---
# <a name="accessing-the-text-buffer-by-using-the-legacy-api"></a>Eski API'yi Kullanarak Metin Arabelleğine Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin, metin akışlarını ve dosya kalıcılığını yönetmekten sorumludur. Arabellek diğer biçimleri okuyup yazabilir, ancak arabellek ile olan tüm sıradan iletişim Unicode kullanılarak gerçekleştirilir. Eski API 'lerde, metin arabelleği, arabellekteki karakter konumlarını belirlemek için bir veya iki boyutlu bir koordinat sistemi kullanabilir.  
  
## <a name="one--and-two-dimension-coordinate-systems"></a>Tek ve Iki boyutlu koordinat sistemleri  
 Tek boyutlu koordinat konumu, arabellekteki ilk karakterden (147 gibi) bir karakterin konumunu temel alır. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream>Arabellekte tek boyutlu bir konuma erişmek için arabirimini kullanırsınız. İki boyutlu koordinat sistemi, çizgi ve Dizin çiftlerine dayalıdır. Örneğin, 43 konumundaki arabellekteki bir karakter, 5.43 satırda, bu satırdaki ilk karakterin sağında beş karakterden oluşmalıdır. Arabirimi kullanarak arabellekte iki boyutlu bir konuma erişirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> . Hem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> hem de <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStream> arabirimleri metin arabelleği nesnesi () tarafından uygulanır <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ve kullanılarak birbirleriyle erişilebilir `QueryInterface` . Aşağıdaki diyagramda bu ve diğer temel arabirimler gösterilmektedir <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> .  
  
 ![Metin arabelleği nesnesi](../extensibility/media/vstextbuffer.gif "vsTextBuffer")  
Metin arabelleği nesnesi  
  
 Koordinat sistemi metin arabelleğinde çalışsa da, iki boyutlu koordinatları kullanmak en iyi duruma getirilir. Tek boyutlu koordinat sistemi, performans yükü oluşturabilir. Bu nedenle, mümkün olan her durumda iki boyutlu koordinat sistemini kullanın.  
  
 Metin arabelleğinin ikinci sorumluluğu dosya kalıcılığı. Bunu yapmak için, metin buffer nesnesi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2> Proje öğeleri ve Kalıcılık ile ilgili diğer ortam bileşenleri için belge veri nesnesi bileşeni olarak davranır ve çalışır. Daha fazla bilgi için bkz. [Proje öğelerini açma ve kaydetme](../extensibility/internals/opening-and-saving-project-items.md).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Eski API'yi Kullanarak Görünüm Ayarlarını Değiştirme](../extensibility/changing-view-settings-by-using-the-legacy-api.md)  
 Eski API kullanılarak Görünüm ayarlarının nasıl değiştirileceğini açıklar.  
  
 [Genel Ayarları İzlemek İçin Metin Yöneticisini Kullanma](../extensibility/using-the-text-manager-to-monitor-global-settings.md)  
 Genel ayarları izlemek için metin Yöneticisi 'nin nasıl kullanılacağını açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Temel Düzenleyicinin İçinde](../extensibility/inside-the-core-editor.md)
