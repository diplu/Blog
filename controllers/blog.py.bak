# -*- coding: utf-8 -*-
# try something like
@auth.requires_membership('blogger')
def post():
    form=SQLFORM(db.blog).process()
    return locals()
@auth.requires_login()
def view():
    rows=db(db.blog).select(orderby=~db.blog.id)
    return locals()
def display_form():
    form=SQLFORM(db.blog)
    if form.process().accepted:
        session.flash='form accepted'
        redirect(url('thanks'))
    elif form.errors:
        response.flash='form has error'
    else:
        response.flash='plase fill out the form'
    return locals()
@auth.requires_membership('blogger')
def update():
    record=db.blog(request.args(0)) or redirect(URL('post'))
    form=SQLFORM(db.blog, record)
    if form.process().accepted:
        response.flash=T('Record update')
    else:
        response.flash=T('plase complete the form')
    return locals()
def index():
    return dict(message="hello from blog.py")
