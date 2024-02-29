# cs300

What was the problem you were solving in the projects for this course?

The problem that was being solved was being able to read, parse, sort and print a list of courses.


How did you approach the problem? Consider why data structures are important to understand.

Since we were expected to print a sorted list, I opted for a binary tree since it would sort the items as they were added in. Different data structures provide different pros and cons to data. Each structure has a different runtime and they have different features that would be useful to different data types and data limitations and requirements. 


How did you overcome any roadblocks you encountered while going through the activities or project?

I researched a lot of different c++ applications and watched many videos on how to do different things with the code. I also, at times, would reference the help in the program I was working in to see what bugs were occurring and how to fix them. 


How has your work on this project expanded your approach to designing software and developing programs?

This has helped expand the different data structures i know but also how to use the different types. It has also helped me understand how sorting and different actions on data affect the data as a whole as well as runtime and memory.


How has your work on this project evolved the way you write programs that are maintainable, readable, and adaptable?

It has helped that I know the different types of data structures to use and which will be most efficient based on requirements. When data is maintained it can run at its best.


Analysis
There are many advantages and disadvantages to using any of the data structures. Vectors are easy to add and remove at the end, and there are locations for each of the items. However, adding and removing in the middle can add more time to process as it has to shift each index for the remaining items. Hash tables improve a lot on vectors, making inserting and deleting items easier since it only must update an array item to insert or delete. The tables, though, can fill up quickly with a lot of data and have collisions resulting in slower results. Lastly, trees can be easy to insert and generally keep the items in order when placed in the tree; since they are already sorted, you can print from the leftmost side to the right, and all the items are ready. Trees can become unbalanced if the information is set in a previously sorted order. They also require pointers since all the items are connected, using more memory.

Recommendations
	I recommend using the trees data structure as one of the requirements is to have the courses printed in alphanumeric order, and trees do that as items are added. They are simple to insert new information, and since the courses will most likely remain the same for a long time, deleting will not be used much. While vectors were also a great option since the runtime analysis only includes adding and creating, it has a more attractive cost; when we factor in the sorting, it will end up being much higher. Since they all have an exact line cost, they all are O(n) for runtime since some lines will have multiple executable lines. Trees have the second lowest cost and already include sorting, resulting in less overall time.

void BinarySearchTree::addNode(Node* node, Course course) {

    // adds to the left side
    if (node->course.courseNum.compare(course.courseNum) > 0) {
        if (node->left == nullptr) {
            node->left = new Node{ course };
        }

        // traverse down
        else {
            this->addNode(node->left, course);
        }
    }
    // add to the right side
    else {
        if (node->right == nullptr) {
            node->right = new Node{ course };
        }
        // traverse down
        else {
            this->addNode(node->right, course);

        }
    }

}

void BinarySearchTree::inOrder(Node* node) {

    // pre order root
    if (node != nullptr) {
        inOrder(node->left);

        // prints out course info
        cout << node->course.courseNum << ": "
            << node->course.title << " | "
            << node->course.prereq1 << "  "
            << node->course.prereq2 << endl;

        // moves to next node
        inOrder(node->right);
    }
}
