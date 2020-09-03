---
title: Kullanarak yalıtılmış Kabuğu değiştirme. Vsct dosyası | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, isolated mode%2C .vsct file
ms.assetid: 6d147c2d-10e9-400e-b8ce-5566287b41ba
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8c106a04e809e772ac3b8a77192fb2f101161e9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194226"
---
# <a name="modifying-the-isolated-shell-by-using-the-vsct-file"></a>.Vsct Dosyası Kullanarak Yalıtılmış Kabuğu Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio yalıtılmış Kabuk projesi için Kullanıcı Arabirimi projesi, uygulamada hangi uygulama gruplarının ve bireysel komutların kullanılabilir olduğunu belirtmenize imkan tanıyan bir. vsct dosyası içerir. Aşağıda, değiştirilmemiş bir. vsct dosyasındaki bir alıntı verilmiştir.  
  
```  
<!-- <Define name="No_WindowListCommand"/> -->  
<!-- <Define name="No_MoreWindowsCommand"/> -->  
<!-- <Define name="No_PaneNextPaneCommand"/> -->  
<!-- <Define name="No_PanePrevPaneCommand"/> -->  
```  
  
 Varsayılan olarak, çoğu komut ve komut grubu dahil edilmiştir. Bir komutu veya komut grubunu dışlamak için, bu komutun veya grubun açıklamasını basitçe kaldırın.  
  
 Örneğin, bir sonraki bölmeyi ve önceki bölme komutlarını kaldırmak için, `No_PaneNextPaneCommand` ve girişlerinin açıklamasını kaldırın `No_PanePrevPaneCommand` :  
  
```  
  
<Define name="No_PaneNextPaneCommand"/> <Define name="No_PanePrevPaneCommand"/>  
  
```  
  
 Daha ayrıntılı bir örnek için bu özelleştirmeler için bkz. [Izlenecek yol: temel yalıtılmış Kabuk uygulaması oluşturma](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## <a name="referenced-files"></a>Başvurulan dosyalar  
 Bir uygulama için varsayılan. vsct dosyası aşağıdaki dosyalara başvurur. Bu dosyalar, Visual Studio SDK yükleme dizininin \VisualStudioIntegration\Common\Inc\ alt dizininde bulunur.  
  
|Dosya|Açıklama|  
|----------|-----------------|  
|wbıg. h|Web 'e gözatamıyorum paketine yönelik kullanıcı arabirimi kimlikleri.|  
|AppIDCmdUsed. vsct|Birincil Visual Studio Kullanıcı arabirimi öğeleri için komut tablosu.|  
|Öykünme Torcmdused. vsct|Emacs ve kısa düzenleyici öykünmesi kullanıcı arabirimi öğeleri için komut tablosu.|  
|Vsdebugguid 'ler. h|Komutların, Seçenekler sayfasının ve Visual Studio hata ayıklayıcının diğer özelliklerinin GUID 'Lerini tanımlar.|  
|VsDbgCmdUsed. vsct|Hata ayıklayıcı için komut tablosu.|  
  
 AppIDCmdUsed. vsct dosyası, Application. vsct dosyasında tanımlanan sembolleri temel alan Visual Studio Kullanıcı arabirimi öğelerini içerir.  
  
 Daha fazla bilgi için bkz [. xml komut tablosu tasarlama (. Vsct) dosyaları](../extensibility/internals/designing-xml-command-table-dot-vsct-files.md) ve [VSCT XML şema başvurusu](../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio Yalıtılmış Kabuğu](../extensibility/visual-studio-isolated-shell.md)
