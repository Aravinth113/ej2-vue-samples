<template>
  <div class="control-section">
    <div id="spreadsheet-conditional-formatting">
        <ejs-spreadsheet ref="spreadsheet" :openUrl="openUrl" :saveUrl="saveUrl" :created="created">
            <e-sheets>
                <e-sheet :name="InventoryList">
                    <e-rows>
                        <e-row :height="height">
                            <e-cells>
                                <e-cell index=1 value="Inventory List"></e-cell>
                            </e-cells>
                        </e-row>
                    </e-rows>
                <e-ranges>
                        <e-range :dataSource="dataSource" startCell="A2" ></e-range>
                </e-ranges>
                <e-conditionalformats>
                    <e-conditionalformat type="GYRColorScale" range="C3:C18" ></e-conditionalformat>
                    <e-conditionalformat type="LessThan" cFColor="RedFT" value="8/30/2019" range="F3:F18"></e-conditionalformat>
                </e-conditionalformats>
                    <e-columns>
                        <e-column :width=100></e-column>
                        <e-column :width=158></e-column>
                        <e-column :width=72></e-column>
                        <e-column :width=113></e-column>
                        <e-column :width=113></e-column>
                        <e-column :width=97></e-column>
                        <e-column :width=73></e-column>
                    </e-columns>
                </e-sheet>
            </e-sheets>
        </ejs-spreadsheet>
    </div>
<div id="action-description">
    <p>
        This sample demonstrates about the conditional formatting features like highlight cell rules, data bars, color scales, and icon sets by using the inventory list details.
    </p>
</div>
<div id="description">
    <p>
        This feature allows you to format a cell or range of cells based on the conditions applied. You can enable or disable conditional formats by using the <code>allowConditionalFormat</code> property.
    </p>
    <p>
        In this sample, we have applied conditional formatting color scales in Quantity column, data bars in Purchase price and selling price column, highlight cell rules in last updated column and rating icon sets applied in rating column by using the <code>conditionalFormat</code> method and <code>conditionalFormats</code> property in sheets model.
    </p>
    <p>
        More information about the Spreadsheet component can be found in this
        <a target="_blank" href="https://ej2.syncfusion.com/documentation/spreadsheet/getting-started">
            documentation</a> section.
    </p>
</div>
  </div>
</template>
<!-- custom code start -->
<style>
    .control-section .control-wrapper {
        height: 550px;
    }

    #sb-content .e-spreadsheet .e-tab .e-tab-text {
        display: inherit;
    }

    #spreadsheet-conditional-formatting {
      height: 550px;
    }

    .ej2-new .control-section {
        height: 550px;
    }
    .e-spreadsheet .e-main-panel .e-main-content{
        margin-left: 0 !important;
    }
</style>
<!-- custom code end -->
<script>
import Vue from "vue";
import { SpreadsheetPlugin } from "@syncfusion/ej2-vue-spreadsheet";
import * as dataSource from "./conditional-formatting-data.json";
Vue.use(SpreadsheetPlugin);
export default Vue.extend({
   data: () => {
    return {
        height: 30,
        InventoryList:"Inventory List",
        dataSource: dataSource.conditionalFormatting,
         openUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/open',
         saveUrl: 'https://ej2services.syncfusion.com/production/web-services/api/spreadsheet/save'
    }
  },
  methods: {
    created: function() {
        var spreadsheet = this.$refs.spreadsheet;
            spreadsheet.merge('A1:G1');
            spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center' }, 'A2:G2');
            spreadsheet.cellFormat({ fontWeight: 'bold', textAlign: 'center', verticalAlign: "middle", fontSize: '13pt' }, 'A1:G1');
            spreadsheet.conditionalFormat({ type: 'BlueDataBar', range: 'D3:D18' });
            spreadsheet.conditionalFormat({ type: 'OrangeDataBar', range: 'E3:E18' });
            spreadsheet.conditionalFormat({ type: 'ThreeStars', range: 'G3:G18' });
            }
        }
});
</script>