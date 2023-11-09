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





frappe.ui.form.on("Sales Order Item", {
    item_code: function(frm, cdt, cdn) {
       var d = locals[cdt][cdn];
        qty_reserved(frm, cdt, cdn);
    },
     setup: function(frm, cdt, cdn) {
        var d = locals[cdt][cdn];
        qty_reserved(frm, cdt, cdn);
    },
 
    projected_qty: function(frm, cdt, cdn) {
        var d = locals[cdt][cdn];
        qty_reserved(frm, cdt, cdn);
    },
    
    actual_qty: function(frm, cdt, cdn) {
      var d = locals[cdt][cdn];
        qty_reserved(frm, cdt, cdn);
    }

});


 function qty_reserved(frm, cdt, cdn) {
     var d = locals[cdt][cdn];
    
    //   var total=d.projected_qty-d.actual_qty;
//       frappe.model.set_value(d.doctype, d.name, 'reserved_qty_new', d.projected_qty - d.actual_qty);
    frappe.model.set_value(d.doctype, d.name, 'reserved_qty_new', d.projected_qty+d.actual_qty);
    refresh_field('reserved_qty_new')
        
     }
