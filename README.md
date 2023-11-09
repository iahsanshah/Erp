# Erp

frappe.ui.form.on('Sales Order Item', {
items_remove: function(frm, cdt, cdn){
var d = locals[cdt][cdn];
var total_amount = 0;
frm.doc.items.forEach(function (d) {total_amount += d.disc_amount;});
frm.set_value('total_discount', total_amount);
refresh_field('total_discount');
    }
});
frappe.ui.form.on('Sales Order Item', {
items_remove: function(frm, cdt, cdn){
var d = locals[cdt][cdn];
var total_amount = 0;
frm.doc.items.forEach(function (d) {total_amount += d.base_amount;});
frm.set_value('total', total_amount);
refresh_field('total');
    }
});
