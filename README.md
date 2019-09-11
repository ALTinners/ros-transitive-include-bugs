# Testing transitive include paths with multiple overlayed workspace packages

The target point of failure is in `b/methods.h`

To test:

1. Build normally with `catkin_make` - it should compile well.
2. Run `bloom-generate rosdebian && debuild -uc -us -b` in `a` and `b`. Then `dpkg -i ../*.deb` from `b` to install
3. Uncomment the different variable in `b`'s header and change the point of reference in `c` and `d`'s src files.
4. On my machine, `c` fails to compile.