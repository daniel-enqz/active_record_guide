# Active Record Best practices
- return an ActiveRecord::Relation
  - chainable instructions
  - always rely in database, not in ruby.
  - Will only be sended when its needed. (.to_sql)

> ### Common retreval ways:
- find
- find_by
- last/first 
- take
- Always prevent sql injection (Project.where(name: "title = ? AND out_of_print = ?", params[:title], params[:oop])) // You can also use symbols 
- Remember you can use methods (or, like, not)

> ### Iterations:
- for_each(batch_size, start:, finish:)
- find_in_batches

> ### Sorting:
- order(created_at: "")
- select and pluck (Sometimes we dont need all the model attributes) [Project.all.pluck(:name)]
- If you want to mantain the active record relation go for select.

> ### Gmore filtering
- common way is doing Project.all.group(:description).count # => {nil: 4, "test": 2}
- having("count(*)")
- Book.joins(:reviews)

> ### Eager Loading
- Skip N + 1 problem
- Use includes
- eager_load()
- preload

> ### Write efficient and chainable scopes
- Scopes need to return A.Record relation!
- Leave ordering out of scopes
- clean naming
- do not scopes datasets in ruby
- default_scope. Comes into use when you need to implement a default query when searching.


![Screenshot 2022-12-15 at 17 25 09](https://user-images.githubusercontent.com/72522628/207987881-2d93474c-3ecb-48b2-be9d-b49774511dd1.jpg)
