# Active Record Best practices
- return an ActiveRecord::Relation
  - chainable instructions
  - always rely in database, not in ruby.

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

> ### Grouping
- common way is doing Project.all.group(:description).count # => {nil: 4, "test": 2}
