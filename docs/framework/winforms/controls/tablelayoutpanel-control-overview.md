---
title: Información general sobre el control TableLayoutPanel
ms.date: 03/30/2017
f1_keywords:
- TableLayoutPanel
helpviewer_keywords:
- controls [Windows Forms], resizing
- resizable controls [Windows Forms]
- Windows Forms controls, proportional resizing
- Windows Forms, proportional resizing of controls
- layout [Windows Forms], TableLayoutPanel control
- TableLayoutPanel control [Windows Forms], about TableLayoutPanel control
ms.assetid: 337661c8-61cb-44ee-93e0-3662bddec327
ms.openlocfilehash: be7ef4055d809349fe97a3d48e29158c5449576b
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855808"
---
# <a name="tablelayoutpanel-control-overview"></a>Información general sobre el control TableLayoutPanel
El control <xref:System.Windows.Forms.TableLayoutPanel> organiza su contenido en una cuadrícula. Como el diseño se realiza en tiempo de diseño y en tiempo de ejecución, puede cambiar dinámicamente cuando cambie el entorno de la aplicación. Esto proporciona a los controles del panel la capacidad de ajustar el tamaño proporcionalmente para poder responder a cambios como el ajuste de tamaño del control primario o el cambio de longitud del texto debido a la localización.  
  
 Cualquier control de Windows Forms puede ser un control secundario del control <xref:System.Windows.Forms.TableLayoutPanel>, incluidas otras instancias de <xref:System.Windows.Forms.TableLayoutPanel>. Esto permite construir diseños sofisticados que se adaptan a los cambios en tiempo de ejecución.  
  
 El control <xref:System.Windows.Forms.TableLayoutPanel> puede expandirse para acomodar nuevos controles cuando se agreguen, dependiendo del valor de las propiedades <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A>, <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> y <xref:System.Windows.Forms.TableLayoutPanel.GrowStyle%2A>. Establecer las propiedades <xref:System.Windows.Forms.TableLayoutPanel.RowCount%2A> o <xref:System.Windows.Forms.TableLayoutPanel.ColumnCount%2A> en un valor de 0 especifica que el <xref:System.Windows.Forms.TableLayoutPanel> se desenlazará en la dirección correspondiente.  
  
 También puede controlar la dirección de expansión (horizontal o vertical) cuando el control <xref:System.Windows.Forms.TableLayoutPanel> se llene de controles secundarios. De forma predeterminada, el control <xref:System.Windows.Forms.TableLayoutPanel> se expande hacia abajo agregando filas.  
  
 Si quiere que el comportamiento de las filas y columnas sea diferente del predeterminado, puede controlar las propiedades de las filas y columnas mediante las propiedades <xref:System.Windows.Forms.TableLayoutPanel.RowStyles%2A> y <xref:System.Windows.Forms.TableLayoutPanel.ColumnStyles%2A>. Puede establecer las propiedades de las filas o columnas individualmente.  
  
 El control <xref:System.Windows.Forms.TableLayoutPanel> agrega las siguientes propiedades a sus controles secundarios: `Cell`, `Column`, `Row`, `ColumnSpan` y `RowSpan`.  
  
 Puede combinar las celdas del control <xref:System.Windows.Forms.TableLayoutPanel> estableciendo las propiedades `ColumnSpan` o `RowSpan` de un control secundario.  
  
1.  [Cómo: Alinear y expandir un control en un control TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2.  [Cómo: Abarcar filas y columnas en un control TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
3.  [Cómo: Editar columnas y filas en un control TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
4.  [Tutorial: Organizar controles en Windows Forms mediante TableLayoutPanel](https://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
## <a name="see-also"></a>Vea también  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutSettings>  
 [Crear un diseño de formularios Windows Forms que sea apropiado para la localización](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Crear Windows Forms de entrada de datos de tamaño variable](../../../../docs/framework/winforms/controls/how-to-create-a-resizable-windows-form-for-data-entry.md)  
 [Procedimientos recomendados para el control TableLayoutPanel](../../../../docs/framework/winforms/controls/best-practices-for-the-tablelayoutpanel-control.md)
