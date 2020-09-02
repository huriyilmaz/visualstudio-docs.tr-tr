---
title: Komut Işleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - command handling
ms.assetid: 78f67d92-77f7-45cb-ad75-6e3346379cc3
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 563f38cd2dc3854918fe637fdc11afe1d1a49b64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184367"
---
# <a name="command-handling"></a>Komut İşleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Düzenleyiciniz yeni komutlar tanımlayabilir. Komutlar genellikle bir menüde, araç çubuğunda veya bir bağlam menüsünde görüntülenir.  
  
 Komutları ve menüleri tanımlama hakkında daha fazla bilgi için bkz. [Komutlar, menüler ve araç çubukları](../extensibility/internals/commands-menus-and-toolbars.md).  
  
 Dil hizmeti, numaralandırmayı kesintiye uğratan, düzenleyicide gösterilen bağlam menülerini denetleyebilir <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> . Alternatif olarak, bağlam menüsünü işaret başına temelinde kontrol edebilirsiniz. Daha fazla bilgi için bkz. [dil hizmeti filtreleri Için önemli komutlar](../extensibility/internals/important-commands-for-language-service-filters.md).  
  
## <a name="adding-commands-to-the-editor-context-menu"></a>Düzenleyici bağlam menüsüne komut ekleme  
 Bağlam menüsüne bir komut eklemek için, önce belirli bir gruba ait olan bir menü komutları kümesi tanımlamanız gerekir. Aşağıdaki örnek, izlenecek yol gözden geçirmesinin bir parçası olarak oluşturulan. vsct dosyasından alınmıştır: [özel düzenleyiciye özellikler ekleme](../extensibility/walkthrough-adding-features-to-a-custom-editor.md):  
  
 \<Menu guid="guidCustomEditorCmdSet" id="IDMX_RTF" priority="0x0000" type="Context">  
  
 \<Parent guid="guidCustomEditorCmdSet" id="0"/>  
  
 \<Strings>  
  
 \<ButtonText>CustomEditor bağlam menüsü\</ButtonText>  
  
 \<CommandName>CustomEditorContextMenu\</CommandName>  
  
 \</Strings>  
  
 \</Menu>  
  
 \</Menus>  
  
 Yukarıdaki metin, **CustomEditor bağlam menüsü**ile bir bağlam menüsü komutu ekler. Menü GUID 'SI, bu düzenleyiciyle oluşturulan ve tür "Context" olan komut kümesinden oluşur.  
  
 . Vsct dosyasında tanımlanması gerekmeyen önceden tanımlanmış komutları da kullanabilirsiniz. Örneğin, Visual Studio paket şablonu tarafından oluşturulan EditorPane.cs dosyasını incelerseniz, tarafından tanımlanan bir dizi önceden tanımlanmış <xref:Microsoft.VisualStudio.VSConstants.VSStd97CmdID> <xref:Microsoft.VisualStudio.VSConstants.GUID_VSStandardCommandSet97> komutun, onSelectAll yöntemi gibi komut işleyicilerde işlendiğini görürsünüz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komutlar, Menüler ve Araç Çubukları](../extensibility/internals/commands-menus-and-toolbars.md)
